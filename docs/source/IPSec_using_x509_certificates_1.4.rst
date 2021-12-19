IPSec Authentication using x509 certificates (VyOS 1.4) 
=======================================================

.. _Task:

Task
----

Create an IPsec VPN tunnel using X.509 certificates in VyOS 1.4.

.. _Introduction:

Introduction
------------

To accomplish this, we need a pair of keys (public & private) and 
the appropriate X.509 certificate for each IPsec peer. We also need 
a self-signed Root CA certificate to validate the peer certificates. 

Proper use of certificates involves creating a PKI infrastructure 
with root and intermediate CAs, certificate revocation validation, 
and other elements. 

In this example, we will use a simplified PKI infrastructure consisting 
only of Root CAs. A VyOS router will be used as the Root CA.

.. _Configuration:

Configuration
-------------

So. There are two VyOS routers (R1 & R2). We need to connect them 
using IPsec with X.509 certificate authentication.

First step. Choose R1 as Root CA. Generate a key pair for the Root CA
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Use Operational Mode commands, not Configuration Mode: 

.. code-block:: console

   vyos@R1:~$ generate pki ca install CA 
   Enter private key type: [rsa, dsa, ec] (Default: rsa) 
   Enter private key bits: (Default: 2048) 
   Enter country code: (Default: GB) 
   Enter state: (Default: Some-State) 
   Enter locality: (Default: Some-City) 
   Enter organization name: (Default: VyOS) 
   Enter common name: (Default: vyos.io) CA 
   Enter how many days certificate will be valid: (Default: 1825) 
   Note: If you plan to use the generated key on this router, do not encrypt the private key. 
   Do you want to encrypt the private key with a passphrase? [y/N] N 
   Configure mode commands to install: 
   set pki ca CA certificate 'MIIDnTCCAo........=' 
   set pki ca CA private key 'MIIEvwIBAD........=' 

This will give you the encryption key pair. Copy the lines with 
the keys and commands to set them (after the output lines 
"Configure mode commands to install"): 

.. code-block::

   set pki ca CA certificate 'MIIDnTCCAo........=' 
   set pki ca CA private key 'MIIEvwIBAD........='



Creating recipes
----------------

To retrieve a list of random ingredients,
you can use the ``lumache.get_random_ingredients()`` function:

.. autofunction:: lumache.get_random_ingredients

The ``kind`` parameter should be either ``"meat"``, ``"fish"``,
or ``"veggies"``. Otherwise, :py:func:`lumache.get_random_ingredients`
will raise an exception.

.. autoexception:: lumache.InvalidKindError

For example:

>>> import lumache
>>> lumache.get_random_ingredients()
['shells', 'gorgonzola', 'parsley']

cxf-kerberos
===========

This project contains a number of tests that show how to use Kerberos with
Apache CXF, where the KDC used in the tests is based on Apache Kerby. 

Note: To disable UDP (for GSS) you can add the following to the krb5.conf:

"udp_preference_limit = 1".

Then edit the tests + change the port substitution from KDC_UDP_PORT to
KDC_PORT.

1) AuthenticationTest

Thie test shows how an Apache CXF JAX-WS service endpoint can authenticate a
client using Kerberos. There are two test-cases contained in
"AuthenticationTest", one that uses a WS-SecurityPolicy KerberosToken policy,
and the other that uses a SpnegoContextToken policy.

Both testcases start up a KDC locally using Apache Kerby. In each case, the
service endpoint has a TransportBinding policy, with a corresponding
EndorsingSupportingToken which is either a KerberosToken or SpnegoContextToken.
The client will obtain a service ticket from the KDC and include it in the
security header of the service request.

2) JAXRSAuthenticationTest

This test shows how to use Kerberos with a JAX-RS service. 


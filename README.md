# MIT_Kerberos_info


To prevent anyone to eavedrop on your data on a unsecure network while providing a means to authenticate a user to use a service - Kerberos can be used. 

KDC ( Key Distribution Center ) supplies the tickets and generates temporary session keys that allow a user to securely authenticate to a service. 
It stores all the secret symmetric keys for users & services. 

AS ( Authentication Server ) confirms that a known user is making an access request and it issues the ticket granting tickets to user.

  Contains User-ID & Client-Secret-Key as a key-value datastore.
  Client sends message to AS 
    message = {
        User-ID,
        Service-ID,
        User-IP-Address,
        Requested lifetime for TGT
      }
      
  AS sends back the Client a message, a TGT & along with these two a ticket granting server secret key. 
    message = {
        TGS-ID,
        Timestamp,
        Lifetime for TGT
        ticket_granting_server_session_key
      } + Client Secret Key 

    ticket_granting_ticket = {
        User-ID,
        TGS-ID,
        Timestamp,
        User-IP-Address,
        Lifetime for TGT
        ticket_granting_server_session_key
      } + TGS Secret Key 

    User receives the first message - to decrypt that message - the user generates a secret key, by entering the password 
    Kerberos adds SALT to the password and the version to the password. -> that generates the user's secret key. 
    
   
TGS ( Ticket Granting Server ) confirms that a user is making access request to a known service & issues service tickets.

  Same as above, this authenticates whether the service is known in its datastore, 
  Then TGS generates the Service ticket and sends the messages back to the user. 
  
There service creates its own authenticator message and sends back to user, therein the 



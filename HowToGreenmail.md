# Greenmail

[Greenmail](http://www.icegreen.com/greenmail/) is an open source suite of email servers supporting SMTP, POP3 and IMAP. 
Any email sent to Greenmail will not go any further, but is stored locally for retrieval via these protocols.  
There is no web interface, so it is necessary to use a mail client like [Thunderbird](https://www.mozilla.org/en-US/thunderbird/).
 
Every time Greenmail receives an email via SMTP, it creates a new email account with the email address as username and password.
Email is not persisted to permanent storage, so every time the server is restarted all email will be discarded. 

By default, Greenmail is set up to use the normal ports plus 10000.

    SMTP: 10025
    POP3: 10110
    IMAP: 10143

## Testing

The Guiceyloops test framework, used by most projects, allows tests to start a Greenmail server to capture emails being sent.
This is done by extending AbstractServerTest and overriding enableMailServer() to return true.  This method returns false by default.

      protected boolean enableMailServer() {
        return true;
      }

The build.yaml file defines the following dependency for use by Guiceyloops:
 
      greenmail: com.icegreen:greenmail:jar:1.4.1

## Development

In development, Greenmail may be used to capture outgoing mail.

The build.yaml file defines the following dependency to start a Greenmail server:
 
      greenmail_server: com.icegreen:greenmail-webapp:war:1.4.1

The buildfile requires the following to deploy Greenmail when running through Idea (the :packaged attribute does the work).

      ipr.add_glassfish_configuration(project,
                                      :server_name => 'Payara 4.1',
                                      :exploded => [project.name],
                                      :packaged => {:greenmail => :greenmail_server})
                                      
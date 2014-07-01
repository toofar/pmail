As an MTA (after setting up ~/.pmailrc or /etc/pmailrc):

    pmail < mymail.mail

To attach some files, set the too address and open an editor then send (if the
file is non-empty):

    pmail -t jim@example.com -s "Please money transfer help." -a instructions.exe -e

To configure the formatting options you can use the Format header (which is
removed before sending, as is the Attach header) or the command line arguments.
The Format header is a comma separated list of any of the following values:
qp,markdown,html,flowed. The help output for the corresponding command line
options for an explanation.

    usage: pmail [-h] [-t foo@example.com] [-s "New TPS Report Templates"]
                 [-a /path/to/TPS.pdf] [-c foo@example.com] [-b foo@example.com]
                 [-f me@example.com] [--server smtp.example.com[:124]]
                 [-e [myeditor]] [-n] [--html] [--markdown] [--flowed] [--no-qp]
                 [foo@example.com]
    
    Required values are To, From, Body and Subject. (If you pass the
    --no-editor argument you only need one of Body and Subject.)
    
    If one of these values are missing (or you passed the --editor argument)
    then the message will be opened up in an editor before sending.
    
    Supports ~/.pmailrc file with contents ie:
        [pmail]
        from = me@example.com
        realname = Joe User
        smtp_url = smtp.example.com
    
    positional arguments:
      foo@example.com       Destination Address
    
    optional arguments:
      -h, --help            show this help message and exit
      -t foo@example.com, --to foo@example.com
                            Destination Address. Can be specified multiple times.
      -s "New TPS Report Templates", --subject "New TPS Report Templates"
                            Subject
      -a /path/to/TPS.pdf, --attach /path/to/TPS.pdf
                            Filename to attach. Can be specified multiple times.
      -c foo@example.com, --cc foo@example.com
                            CC Address. Can be specified multiple times.
      -b foo@example.com, --bcc foo@example.com
                            BCC Address. Can be specified multiple times.
      -f me@example.com, --from me@example.com
                            From address for envelope. Sets From header if absent
                            from message. Overrides pmailrc.
      --server smtp.example.com[:124]
                            SMTP server hostname. Overrides pmailrc
      -e [myeditor], --editor [myeditor]
                            Open message in editor before sending. Even if all the
                            required values are present.
      -n, --no-editor       Don't open an editor if the message is missing a
                            required value.
      --html                Parse the message body as markdown and use that to
                            create a markdown+htmlmultipart message.
      --markdown            Mark the message body as markdown.
      --flowed              Mark and format the message body as format=flowed (see
                            rfc3676).
      --no-qp               Don't format non 7 bit clean (utf8) body parts as
                            Quoted-Printabl, uses '8bit' instead.

Released under the zlib license: http://opensource.org/licenses/Zlib

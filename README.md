# sekreto

Store secrets in encrypted plain-text files. Files can be encrypted in the way
of your choice, but by default GPG will be used, similarly to how pass uses it.

This is just an idea, for now, so it lacks any form of implementation.

## Example

```yml
metadata: # perhaps
    name: Vault 1                       # name of the vault
    description: (No description given) # description of the vault

secrets:
    - header: Office computer
      icon:   computer
        - type:     text/plain      # future
          tag:      username        # user-specified datum name
          obscured: false           # whether to intially obscure or not
          value:    john.mcp        # actual secret
        - type:     text/plain
          tag:      password
          obscured: true            # passwords are normally initially obscured
          value:    boatsnhoes
        - type:     text/plain      # an unlimited amount of fields can be
                                    # appended to a header
          tag:      e-mail
          obscured: false
          value:    john.mcpherson@office.sw 
        - type:     totp            # built-in support for TOTP 2FA
          tag:      intranet TOTP
          obscured: false
          digits:   6
          hash:     sha1
          spec:     RFC 6238
          secret:   9H5C4My9xccvdpFFy7bOX595D7sTBGV7

    - header: Home                  # an unlimited amount of headers can be
                                    # stored
      icon:   computer
        - type:     text/plain
          tag:      username
          obscured: false
          value:    jonsnow
        - type:     text/plain
          tag:      password
          obscured: true
          value:    winterfell

    - header: Treasure map
        - type:     image/png
          tag:      Map
          obscured: true
          blob:     blob01

blobs:  # perhaps binary objects, such as images or other important files can
        # also be handled as secrets
    - ref: blob01
      data: vuKaKZXcLTENLUxkbscuotTA4nFdvts4tPiCg9EU8YkrGYTFzZ8Xh18GUNQBNkFk8mZZ6tjnonuFnvXZEBrWlqL7iIXWEjspIgCpzyShGhMugrydmsguaHbJJFWfXq4vVIE5OnPZsOmqz5bhzANctEozMQhRpAlOJKbKpNFHJwlWYeiJhx9Gm7poBz1pWuE7Sdc13IKt
```

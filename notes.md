# NOTES

What's been done:

 - removed delay in svr-auth.c on an incorrect auth to speed up testing

 - moved all sess references to the heap



## Changing to heap:

change `extern struct serversession ses;` to `extern struct serversession* ses;` and with cli_ses in session.h and common-session.c

Then malloc it in svr-main.c


# Replace all "ses" structs with pointers
`find ./ -name "*.c" | xargs sed -iR "s/\([^_]\)ses\./\\1ses->/g"`

`find ./ -name "*.h" | xargs sed -iR "s/\([^_]\)ses\./\\1ses->/g"`

`find ./ -name "*.c" | xargs sed -i "s/^ses\./^ses->/g"`

`find ./ -name "*.h" | xargs sed -i "s/^ses\./^ses->/g"`

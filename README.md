DDEV Add-on Xdebug Trigger
==========================

Usually xdebug is enabled in [ddev](https://ddev.com/) projects by executing
`ddev xdebug` at the host system. This enables xdebug with the setting `xdebug.start_with_request = yes`,
which means it is running on all cli scripts and web requests.

This is not always desired. For example if there are long running php scripts,
cronjobs, etc.

This add-on addresses the issue by setting `xdebug.start_with_request` to `trigger`.

How to trigger Xdebug?
----------------------

### In Command Line

If you are in CLI context (after running `ddev ssh`) you have two aliases to
start and stop xdebug:

    xdebug-start

Sets the env variables `XDEBUG_MODE=debug` and `XDEBUG_SESSION=1` in the current
shell, which enables Xdebug in PHP processes started afterwards in the same shell.

To remove the environment variables again, run

    xdebug-stop

which will effectively stop Xdebug.

This behaviour is explained in Xdebug's [documentation](https://xdebug.org/docs/step_debug#activate_debugger).

### In Web Context

To trigger Xdebug in a web request an `XDEBUG_SESSION` parameter has to be provided
by a query or post parameter or by a cookie.

There are browser extensions, which provides this feature. You'll find the links
at Xdebug's [documentation](https://xdebug.org/docs/step_debug#web-application).

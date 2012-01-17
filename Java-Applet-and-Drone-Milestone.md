Implement a malicious Java applet that uses code from JavaPayload by Michael Schierl. The first round has been implemented but is not functional. The applet will turn the machine running the browser into a drone under the control of BeEF.

After the successful deployment of a drone, the framework can send instructions to:

 * Download and execute file
 * DNS Spoof ()
 * Inject BeEF Hooks into HTTP traffic (possibly just injecting google-analytics.com)

Issues for this milestone are detailed here:
https://github.com/beefproject/beef/issues?sort=created&labels=Java+Applet&direction=asc&state=open
and here:
https://github.com/beefproject/beef/issues?labels=RFC1918+Hijack&sort=created&direction=asc&state=open&page=1
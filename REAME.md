# SCION HTTP Proxy
Uses the SCION HTTP client and server implementation from https://github.com/martenwallewein/quic-go. HTTP Requests can be proxied from SCION to HTTP1 or from HTTP1 to SCION.

## Example  Usage
We have two ASes, 1) `19-ffaa:1:bcc,[141.44.25.152]` and 2) `19-ffaa:1:d00,[49.12.6.5]`.

On 1): Proxy from SCION
`SCION_CERT_KEY_FILE=/home/pi/mgartner/key.pem SCION_CERT_FILE=/home/pi/mgartner/cert.pem home/pi/mgartner/scionhttpproxy --local="19-ffaa:1:bcc,[141.44.25.152]:9001" --remote="http://141.44.25.152:8899" --direction=fromScion --cert /home/pi/mgartner/cert.pem --key /home/pi/mgartner/key.pem`

On 2): Proxy to SCION
`SCION_CERT_KEY_FILE=/opt/scion/key.pem SCION_CERT_FILE=/opt/scion/cert.pem /opt/scion/scionhttp --remote="19-ffaa:1:bcc,[141.44.25.152]" --local="19-ffaa:1:d00,[49.12.6.5]" --localurl="49.12.6.5:81" --direction=toScion`


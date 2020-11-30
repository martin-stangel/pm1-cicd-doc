This script is able to execute command for Jenkins slaves via Jenkins REST API.
It is able to start/stop a node and read or write node's preference.

In order to be able to run the script, please install required dependencies:

```bash
pip install -r requirements.txt
```

## Credentials

`jenkins_client.py` script allows to pass credentials both as command line
arguments and from enviromental variables `JENKINS_URL`, `JENKINS_USER`,
`JENKINS_PASSWORD`. Due to security reasons environmental variables should be
preferred.

**WARNING**: `JENKINS_PASSWORD` must not contain password but access token,
otherwise commands fail.

## Example of usage

Assuming that `JENKINS_URL`, `JENKINS_USER`, `JENKINS_PASSWORD` are
set as environmental variables, the script can be used like this:

```bash
# Stop client
./jenkins_client.py --stop "stop message" pm1-ci9.dmz.whitestein.com

# Start client
./jenkins_client.py --start pm1-ci9.dmz.whitestein.com

# Set preference to 2
./jenkins_client.py --set-preference 2 pm1-ci9.dmz.whitestein.com

# Print current preference (for all nodes)
./jenkins_client.py --get-preference all
```

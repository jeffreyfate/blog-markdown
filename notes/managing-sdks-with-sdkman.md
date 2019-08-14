[![Screen Shot 2019-07-08 at 7.33.04 AM.png](https://svbtleusercontent.com/u3BUrMAWXFUFSk4Ck2GUhs0xspap_small.png)](https://svbtleusercontent.com/u3BUrMAWXFUFSk4Ck2GUhs0xspap.png)

SDKMAN! manages parallel versions of SDKs for Unix based systems. It makes for easy installing, switching, removing, and listing SDK versions.

Installing is easy:

`curl -s "https://get.sdkman.io" | bash`
`source "$HOME/.sdkman/bin/sdkman-init.sh"`
`sdk version`
[![Screen Shot 2019-07-08 at 7.37.00 AM.png](https://svbtleusercontent.com/v4GNJudXeQm9PorCfmZsrE0xspap_small.png)](https://svbtleusercontent.com/v4GNJudXeQm9PorCfmZsrE0xspap.png)

To install the latest Java SDK available via SDKMAN! via the CLI:

`sdk install java`

[![Screen Shot 2019-07-08 at 7.39.06 AM.png](https://svbtleusercontent.com/r9dmMJQMLBx29z7e6XAzez0xspap_small.png)](https://svbtleusercontent.com/r9dmMJQMLBx29z7e6XAzez0xspap.png)

As of this writing, SDKMAN! defaults to the Azul Zulu JDK 11. To see all the JDK candidates, run `sdk ls java`.
[![Screen Shot 2019-07-08 at 7.57.43 AM.png](https://svbtleusercontent.com/osCPK46KUd1M15hdV2zZ7N0xspap_small.png)](https://svbtleusercontent.com/osCPK46KUd1M15hdV2zZ7N0xspap.png)
Install the distribution and version of your choice:

`sdk i java 12.0.1-zulu`

[![Screen Shot 2019-07-08 at 8.07.29 AM.png](https://svbtleusercontent.com/3Kf3W7y42e2Rk4Y9Bf2Fjj0xspap_small.png)](https://svbtleusercontent.com/3Kf3W7y42e2Rk4Y9Bf2Fjj0xspap.png)

There are some other features of SDKMAN!, but that's the 20% that will get you 80% of what you need.

# 🐾
# FSO end-to-end testing using Protractor with Mocha/Chai

### Useful resources:

- [`Protractor API docs`](http://www.protractortest.org/#/api)
- [`Guide to selenium/webdriver actions (mousemove, drag n drop, keyup, etc`](http://seleniumhq.github.io/selenium/docs/api/javascript/module/selenium-webdriver/lib/actions_exports_ActionSequence.html)
- [`Xpath cheat sheet (for element selectors)`](http://ricostacruz.com/cheatsheets/xpath.html)
- [`Chai TDD/BDD assertion docs`](http://chaijs.com/api/bdd/)
- [`chai-string plugin assertion docs`](http://chaijs.com/plugins/chai-string/)
- [`chai-as-promised plugin assertion docs`](http://chaijs.com/plugins/chai-as-promised/)
- [`XPath Helper - Chrome extension to find/evaluate XPath queries`](https://chrome.google.com/webstore/detail/xpath-helper/hgimnogjllphhhkhlmebbmlgjoejdpjl)

# Running the e2e tests independent of a local vagrant installation

- Have git installed [`https://git-scm.com/downloads`](https://git-scm.com/downloads)
- Have node installed [`https://nodejs.org/en/download/`](https://nodejs.org/en/download/)
- Using the "git bash" command line that comes with git, make sure you can run the `npm` command.  If not, add it to your PATH. In windows it will probably be "/c/Program Files/nodejs". It may be required to close the git bash console and open a new one,  after the node installation is complete.
- Download the archive or clone the git repo (@https://github.com/Invotas/fso-qa-test). In case of archive; extract it. Change to the created directory and run "npm install"
- Run the command `node_modules/protractor/bin/webdriver-manager update`
- After the installation is complete, edit `protractor.conf.coffee` and change the following variables/arguments to point to where you want to run the tests against: `baseUrl`, `params.target.version`, `params.login.user`, and `params.login.password`. For `params.ssh.baseIP` and `params.ssh.user` provide the IP-address and Username for the test virtual machine.
- You can now run the tests with the following command `node_modules/protractor/bin/protractor protractor.conf.coffee --suite <suitename>`  (currently, suite name can be either, `standard` which performs end-to-end testing that should work on any installation/snapshot, `test` which allows for testing a specfic spec file)
- Some environments might need to open a second git bash prompt and run `node_modules/protractor/bin/webdriver-manager start`before running the tests

# Test results integration with Testrail
- The feature is available to automatically push test results to testrail where a 'test run' is created at runtime.
- To enable the synchronization with testrail set `params.testrail.bool_enabled` option in the config file to 'true'.
- Configure testrail by entering the testrail url in `params.testrail.url`, the account username in `params.testrail.username`
  and the account password in `params.testrail.password`
# develop

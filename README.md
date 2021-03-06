# Pursuance

## WARNING

Do not expose the server in this branch (`develop`) to the world; for
the moment, it is meant for presentation/demonstration purposes only,
as we are proparing to demo this software and to have users test it
locally before adding a combination of cryptographic auth and
PostgREST's JWTs (JSON Web Tokens) shortly after our demo on November
4, 2017.  Hang tight!


## Getting Started

Please fork and clone down this repository to your local machine.

If you don't have React.js globally installed, run this command:

```
npm install -g create-react-app
```

Next, `cd` into the `pursuance` folder.

Run this command to install node modules:

```
npm install
```

To run the React App on localhost and watch for updates:

```
npm run start
```

Then, in another terminal, to set up the database and run PostgREST,
which our Go code uses for persistence, run:

``` $ cd db/ ```

If you're on Linux, now run

``` $ sudo -u postgres bash init_sql.sh ```

On Mac OS X, instead run

``` $ sudo -u $USER bash init_sql.sh ```

(The following commands should be run regardless of whether you're on
Linux or OS X.)

``` $ postgrest postgrest.conf ```

Then, in another terminal session run this (**an error about not
finding `github.com/PursuanceProject/pursuance` is OK here**) --

``` $ go get ./... ```

``` $ npm run build ```

``` $ go build ```

``` $ ./pursuance ```

Then view <http://localhost:8080>.


## Conventions

Please follow these naming and spacing conventions when submitting a pull request:
[React + Redux Conventions](https://unbug.gitbooks.io/react-native-training/content/45_naming_convention.html).


## Code style and format

We use a combination of [Prettier](https://prettier.io/docs/en/index.html) and [Eslint](https://eslint.org/docs/user-guide/getting-started). Prettier is an opinionated code formatter but does not care about code-quality rules. It only concerns formatting rules. This is why we use Eslint for code-quality rules but not for formatting rules. Read more about the difference between linters and Prettier here: <https://prettier.io/docs/en/comparison.html>. Not ever do we want formatting rules in the `.eslintrc` configuration file. Not implicitly or explicitly. To make sure of that we have a NPM script called verify-eslint-rules (`npm run verify-eslint-rules`) that gives an error if there are Eslint rules somewhere in our `.eslintrc` configuration that conflicts with Prettiers formatting rules.

Before submitting PRs, please fix and format your code using `npm run lint`.


## NPM scripts

Besides from the script [generated by create-react-app](https://github.com/facebookincubator/create-react-app/blob/master/packages/react-scripts/template/README.md#available-scripts) (`npm start`, `npm test`, `npm run build` and `npm run eject`) we have several custom scripts as well:

- `lint` - Runs linting with the `--fix` flag AND formats the code with Prettier (**please run this against your code before submitting PRs**).
- `lint:check` - Just checks the code for lint errors (Eslint only).
- `format` - Automatically fixes the code to fit Prettiers format rules.
- `format:check` - Just checks the code for format errors (Prettier only).
- `ci` - The purpose of this script is to be executed in a CI platform for every pull request. It checks linting, code format and makes sure that there are not any Eslint rules that conflicts with Prettier format rule.

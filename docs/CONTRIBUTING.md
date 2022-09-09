# Contributing

When contributing to this repository, please first discuss the change you wish to make via issue, email, or any other
method with the owners of this repository before making a change.

## Development environment setup

> **[?]**
> Proceed to describe how to setup local development environment.
> e.g:

To set up a development environment, please follow these steps:

1. Clone the repo

   ```sh
   ~$ git clone https://github.com/orkim/gpg-book
   ```

2. Create a virtual environment and install the required dependencies

   ```sh
   ~/gpg-book$ cd gpg-book
   ~/gpg-book$ virtualenv venv
   ~/gpg-book$ source venv/bin/activate
   (venv) ~/gpg-book$ pip install sphinx sphinx-book-theme myst-parser
   ```

3. Now build the documentation locally

   ```sh
   (venv) ~/gpg-book$ make html
   ```

4. Open `~/gpg-book/build/html/index.html` to review changes made

## Issues and feature requests

You've found a bug in the examples, a mistake in the documentation, or maybe you'd like a new feature? You can help
us by [submitting an issue on GitHub](https://github.com/orkim/gpg-book/issues). Before you create an issue, make sure
to search the issue archive -- your issue may have already been addressed!

Please try to create bug reports that are:

- _Specific._ Include as much detail as possible: which version, what environment, etc.
- _Unique._ Do not duplicate existing opened issues.
- _Scoped to a Single Bug._ One bug per report.

**Even better: Submit a pull request with a fix or new feature!**

### How to submit a Pull Request

1. Search our repository for open or closed
   [Pull Requests](https://github.com/orkim/gpg-book/pulls)
   that relate to your submission. You don't want to duplicate effort.
2. Fork the project
3. Create your feature branch (`git checkout -b feat/amazing_feature`)
4. Commit your changes (`git commit -m 'feat: add amazing_feature'`) The GnuPG Book Project
   uses [conventional commits](https://www.conventionalcommits.org), so please follow the specification in your commit
   messages.
5. Push to the branch (`git push origin feat/amazing_feature`)
6. [Open a Pull Request](https://github.com/orkim/gpg-book/compare?expand=1)

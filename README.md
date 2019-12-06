# Introduction

Simple self-contained Flask application which uses `requests_oauthlib` and Warwick's [OAuth support](https://warwick.ac.uk/services/its/servicessupport/web/sign-on/help/oauth/apis) in single-sign on.

Demonstrates how to log users in, retrieve basic attributes and fetch information from a Warwick application (in this case, from [Tabula](https://github.com/UniversityofWarwick/tabula)).


# Usage:

Fill in your consumer key and secret within `main.py`. You can [request](https://warwick.ac.uk/services/its/servicessupport/web/sign-on/help/oauth/apis/registration/) these from the web development team. This code assumes you're using a shared consumer secret (HMAC-SHA1), so don't provide a certificate.

Run the app: `python3 main.py`

To get started, visit: http://127.0.0.1:8091/oauth/begin

Click the grant access button, you'll be redirected back to receive a UUID from the Flask app. The UUID is tied to the access token/secret. In this example repository they're just stored in a Python dictionary. In a real app you'd use a database.

For example, say the UUID is `1b49ee4e-16de-11ea-8625-00d86136d1aa`, substitute it into the UUID parameter in the URLs below:

Now, visit:

http://localhost:8091/oauth/userInfo?uuid=1b49ee4e-16de-11ea-8625-00d86136d1aa

This will give you user information from single-sign on.

http://localhost:8091/oauth/tabula/events/?uuid=1b49ee4e-16de-11ea-8625-00d86136d1aa

This might show you some events from your Tabula timetable (if you have any).

Another example, fetching assignments:

http://localhost:8091/oauth/tabula/assignments/?uuid=1b49ee4e-16de-11ea-8625-00d86136d1aa



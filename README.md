# README

Hello there, I have some notes for this one.

### Tech:
- Ruby 3.1.1p18
- Rails 7.0.3
- MySQL 5.7

### Gem used:
- Devise
- Devise-jwt

There's plenty of choices for jwt in Rails, and I think they're all not really complete. So if we really want to go with the best approach, I think we can choose to build it by ourselves, which will take longer than expected.

I went through these gems' documentation to see what's better:
- Devise-jwt
- Devise_token_auth
- doorkeeper
- api_guard

I picked the solution to use Devise & Devise-jwt because
- It's convenient.
- Devise is quite common so the support from community will be better than other gems.
- The documentation is better than other gems.
- The other gems I barely use, so this is another reason devise is better with the limited timeline.

And actually, it does not have the refresh token feature yet, and this is a con. E.g `api_guard` has it, but we'll have to define the white list feature if we need it. And I considered building the Refresh Token feature is a okay choice, plus we have better community support.

P/S: For the purpose of showing about JWT, I chose dotenv to use ENV for convenience, but definitely Rails Encrypted Credentials is a better choice.

### How to run this
This is just a pretty simple repo, but I'll still specify how to run it here:

Install all necessary things:
- Ruby 3.1.1p18
- bundler 2.3.7
- MySQL 5.7

```
bundle install
bin/rails db:create db:migrate
cp .env.development .env
bin/rails s
```

- Go to `http://localhost:3000/users/sign_up` to create a user
- Sign in `http://localhost:3000/users/sign_in` to login
- You can check the access token inside the Authorization header from the Response. Thank you!
- Just a note, I put `jwt_revocation_strategy` in the model but it does not set up as expected yet.

Thank you for your time.

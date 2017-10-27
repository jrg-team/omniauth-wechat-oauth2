Omniauth-wechat-oauth2
======================

[![Build Status](https://travis-ci.org/skinnyworm/omniauth-wechat-oauth2.svg)](https://travis-ci.org/skinnyworm/omniauth-wechat-oauth2) [![Gem Version](https://badge.fury.io/rb/omniauth-wechat-oauth2.png)](http://badge.fury.io/rb/omniauth-wechat-oauth2)

Wechat OAuth2 Strategy for OmniAuth 1.0. 

You need to get a wechat API key at: http://mp.weixin.qq.com

Wechat oauth2 specification can be found at: http://mp.weixin.qq.com/wiki/index.php?title=网页授权获取用户基本信息

## Installation

Add to your `Gemfile`:

```ruby
gem "omniauth-wechatpc-oauth2"
```

Then `bundle install`.


## Usage

Here's an example for adding the middleware to a Rails app in `config/initializers/omniauth.rb`:

```ruby
Rails.application.config.middleware.use OmniAuth::Builder do
  provider :wechatpc, ENV["WECHAT_APP_ID"], ENV["WECHAT_APP_SECRET"]
end
```

You can now access the OmniAuth Wechat OAuth2 URL: `/auth/wechat`

## Configuration

You can configure several options, which you pass in to the `provider` method via a hash:

* `scope`: Default is "snsapi_login"

For devise user, you can set up scope in your devise.rb as following.

```ruby
config.omniauth :wechatpc, ENV["WECHAT_APP_ID"], ENV["WECHAT_APP_SECRET"]
```

## Auth Hash

Here's an example of an authentication hash available in the callback by accessing `request.env["omniauth.auth"]`:

```ruby
{
    :provider => "wechatpc",
    :uid => "123456789",
    :info => {
      nickname:   "Nickname",
      sex:        1,
      province:   "Changning",
      city:       "Shanghai",
      country:    "China",
      headimgurl: "http://image_url"
    },
    :credentials => {
        :token => "token",
        :refresh_token => "another_token",
        :expires_at => 7200,
        :expires => true
    },
    :extra => {
        :raw_info => {
          openid:     "openid"
          nickname:   "Nickname",
          sex:        1,
          province:   "Changning",
          city:       "Shanghai",
          country:    "China",
          headimgurl: "http://image_url"
        }
    }
}
```





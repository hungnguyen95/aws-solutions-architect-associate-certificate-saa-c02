# 2. CNAME and ALIAS

# CNAME vs Alias

- AWS Resources (Load Balancer, CloudFront, etc…) expose an AWS URL: `lb1-1234.us-east-2.elb.amazonaws.com` and you want it to be `myapp.mydomain.com`
- CNAME:
    - Points a URL to any other URL. ([`app.mydomain.com`](http://app.mydomain.com/) => [`blabla.anything.com`](http://blabla.anything.com/))
    - **ONLY FOR NON ROOT DOMAIN (aka. [something.mydomain.com](http://something.mydomain.com/))**

        It has to be `***.mydomain.com` (non root domain)

        It cannot be `[mydomain.com](http://mydomain.com)` (root domain)

- Alias:
    - Points a URL to an AWS Resource ([`app.mydomain.com`](http://app.mydomain.com/) => [`blabla.amazonaws.com`](http://blabla.amazonaws.com/))
    - **Works for ROOT DOMAIN and NON ROOT DOMAIN (aka [mydomain.com](http://mydomain.com/))**
    - Free of charge
    - Native health check
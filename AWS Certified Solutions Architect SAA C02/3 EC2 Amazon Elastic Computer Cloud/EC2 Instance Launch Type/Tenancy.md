# Tenancy

Any instances has 3 types of tenancy:

- **Shared tenancy:**

    Shared tenancy is the default tenancy model for all Amazon EC2instances, regardless of instance type, pricing model, and so forth. Shared tenancy means that a single host machine may house instances from different customers. As AWS does not use overprovisioning and fully isolates instances from other instances on the same host, this is a secure tenancy model.

- **Dedicated Instance:**

    Dedicated Instances run on hardware that’s dedicated to a single customer. As a customer runs more Dedicated Instances, more underlying hardware may be dedicated to their account. Other instances in the account (those not designated as dedicated)will run on shared tenancy and will be isolated at the hardware level from the Dedicated Instances in the account.

- **Dedicated Host:**

    An Amazon EC2 Dedicated Host is a physical server with Amazon EC2instance capacity fully dedicated to a single customer’s use. Dedicated Hosts can help you address licensing requirements and reduce costs by allowing you to use your existing server bound software licenses. The customer has complete control over which specific host runs an instance at launch. This differs from Dedicated Instances in that a Dedicated Instance can launch on any hardware that has been dedicated to the account.
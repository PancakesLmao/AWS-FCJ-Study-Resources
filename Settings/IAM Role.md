A role is a feature of [[AWS Identity and Access Management]]
IAM role can be assumed by the [[IAM User]]
An IAM role is an IAM identity that you can create in your account that has specific permissions. Roles can be granted temporary credentials that have a more restricted set of permissions than your standard IAM user
It is similar to IAM user (Identity and Policies) but instead of being uniquely associated with one person, a role is intended to be **assumable by anyone who needs it**.
A role **DOES NOT have standard long-term credentials such as a password or access keys associated with it**. Instead, when you assume a role, it provides you with **TEMPORARY** security credentials for your role session
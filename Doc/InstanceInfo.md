# User Data #
** Sets up the house before you move in **

# IMDSv2 - Instance Metadata Services version2 #
** You're walking around  the house after move-in, checking things out **


curl -s -H "X-aws-ec2-metadata-token: $(curl -s -X PUT \
  http://169.254.169.254/latest/api/token \
  -H 'X-aws-ec2-metadata-token-ttl-seconds: 21600')" \
  http://169.254.169.254/latest/meta-data/instance-id


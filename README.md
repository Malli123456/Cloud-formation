# Cloud-formation
# SG from bastion
{
    "AWSTemplateFormatVersion": "2010-09-09",
    "Resources": {
        "SGBase": {
            "Type": "AWS::EC2::SecurityGroup",
            "Properties": {
                "GroupDescription": "Base Security Group",
                "SecurityGroupIngress": [
                    {
                        "IpProtocol": "tcp",
                        "CidrIp": "0.0.0.0/0",
                        "FromPort": "22",
                        "ToPort": "22"
                    }
                ]
            }
        },
        "SGBaseIngress": {
            "Type": "AWS::EC2::SecurityGroupIngress",
            "Properties": {
                "GroupName": {
                    "Ref": "SGBase"
                },
                "IpProtocol": "tcp",
                "FromPort": "80",
                "ToPort": "80",
                "SourceSecurityGroupName": {
                    "Ref": "SGBase"
                }
                
            }
        },
        "SGBaseIngress1": {
            "Type": "AWS::EC2::SecurityGroupIngress",
            "Properties": {
                "GroupName": {
                    "Ref": "SGBase"
                },
                "IpProtocol": "tcp",
                "FromPort": "443",
                "ToPort": "443",
                "SourceSecurityGroupName": {
                    "Ref": "SGBase"
                }
                
            }
        }
        
    }
}

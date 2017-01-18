# Grant-HypSecurityGroupEgress

Adds an egress rule to a security group.

## 语法

    Grant-HypSecurityGroupEgress [-LiteralPath] <String> -GroupId <String[]> -Protocol <String> [-FromPort <Decimal>] [-ToPort <Decimal>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    
    Grant-HypSecurityGroupEgress [-LiteralPath] <String> -IPRange <String[]> -Protocol <String> [-FromPort <Decimal>] [-ToPort <Decimal>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
    

## 详细说明

Adding an egress rule permits network traffic from instances within the security group to pass to one or more destination CIDR IP address ranges or security groups.

## 相关命令

- [Amazon AuthorizeSecurityGroupEgress: http://docs.aws.amazon.com/AWSEC2/latest/APIReference/ApiReference-query-AuthorizeSecurityGroupEgress.html](Amazon AuthorizeSecurityGroupEgress: http://docs.aws.amazon.com/AWSEC2/latest/APIReference/ApiReference-query-AuthorizeSecurityGroupEgress.html.html)
- [IANA protocol numbers: http://www.iana.org/assignments/protocol-numbers/protocol-numbers.xhtml](IANA protocol numbers: http://www.iana.org/assignments/protocol-numbers/protocol-numbers.xhtml.html)
- [Grant-HypSecurityGroupIngress](Grant-HypSecurityGroupIngress.html)
- [Revoke-HypSecurityGroupIngress](Revoke-HypSecurityGroupIngress.html)
- [Revoke-HypSecurityGroupEgress](Revoke-HypSecurityGroupEgress.html)

## 参数

| 名称           | 说明                                                                                                                                                                                                                        | 是否必需？ | 管道输入           | 默认值                                   |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | -------------- | ------------------------------------- |
| LiteralPath  | Specifies the full XDHyp provider path to the security group, equivalent to the FullPath property of the security group object. The path can specify a security group relative to a hypervisor conection or hosting unit. | true  | true (ByValue) |                                       |
| 协议           | Specifies the protocol name or number. Protocol numbers can be found at: http://www.iana.org/assignments/protocol-numbers/protocol-numbers.xhtml  
Use -1 to specify all protocols.                                       | true  | false          |                                       |
| GroupId      | Specifies one or more destination security groups to which traffic will be permitted by this rule. This parameter cannot be specified in conjunction with IPRange.                                                        | true  | false          |                                       |
| IPRange      | Specifies one or more destination CIDR IP address ranges to which traffic will be permitted by this rule. This parameter cannot be specified in conjunction with IPRange.                                                 | true  | false          |                                       |
| FromPort     | The start of the port range for port based protocols. For ICMP this specifies the type number.  
Use -1 to specify all ICMP types.                                                                                        | false | false          |                                       |
| ToPort       | The end of the port range for port based protocols. For ICMP this specifies the type number, where -1 can be used to specify all ICMP types.                                                                              | false | false          |                                       |
| LoggingId    | 指定此 cmdlet 调用所属的高级操作的标识符。 Citrix Studio 和 Director 通常创建高级操作。 PowerShell 脚本也可以借助 Start-LogHighLevelOperation 和 Stop-LogHighLevelOperation cmdlet 在高级操作中打包一系列 cmdlet 调用。                                                    | false | false          |                                       |
| AdminAddress | 指定 PowerShell 管理单元将与其连接的 XenDesktop 控制器的地址。可以提供主机名或 IP 地址。                                                                                                                                                                | false | false          | Localhost。一旦有 cmdlet 提供了某个值，此值将变为默认值。 |

## 输入类型

### System.string

The LiteralPath can be piped in.

## 返回值

### 无

## Notes Security groups can be added and removed using the New-Item and Remove-Item cmdlets.

## 示例

### 示例 1

    c:\PS> $Group = New-Item -ItemType SecurityGroup -Path XDHyp:\Connections\AWS -Name MySecurityGroup -Description 'Example group'
              c:\PS> Grant-HypSecurityGroupEgress $Group.FullPath -Protocol '-1' -IPRange '0.0.0.0/16'
    

Description  
\---\---\-----  
Create a security group and grant full egress to anywhere.

### 示例 2

    c:\PS> $Group1 = New-Item -ItemType SecurityGroup -Path XDHyp:\Connections\AWS -Name MySecurityGroup1 -Description 'Example group 1'
              c:\PS> $Group2 = New-Item -ItemType SecurityGroup -Path XDHyp:\Connections\AWS\MySecurityGroup2 -Description 'Example group 2'
              c:\PS> Grant-HypSecurityGroupEgress $Group1.FullPath -FromPort 0 -ToPort 0 -Protocol icmp -GroupId $Group2.Id
              c:\PS> Grant-HypSecurityGroupIngress $Group2.FullPath -FromPort 0 -ToPort 0 -Protocol icmp -GroupId $Group1.Id
    

Description  
\---\---\-----  
Make 2 security groups and permit group 1 to ping group 2.
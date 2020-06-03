

Task 1: Prepare backend

1. lon-dc1 as adatum/administrator
2. AD users and computers: create groups: VPN users; VPN server; NPS server; add lon-host1 and lon-svr1
3. AD CA: Create User Authentication template - steps from
   https://docs.microsoft.com/en-us/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/vpn-deploy-server-infrastructure
4. AD CA: Create the VPN Server Authentication template - steps from link above
5. AD CA: Create the NPS Server Authentication template - steps from link above
6. Group Policy Management: Configure certificate autoenrollment in Group Policy - steps from link above

7. switch to lon-host1 as adatum/administrator
8. lon-host1 - enroll VPN server certificate - https://docs.microsoft.com/en-us/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/vpn-deploy-server-infrastructure  
9. install addtional hyper-v network as "internet"; configure IP address on lon-host1 for "Internet"
10. install RAS gateway VPN server
    Install-WindowsFeature DirectAccess-VPN -IncludeManagementTools
11.  Configure Remote Access as a VPN Server - detailed steps from https://docs.microsoft.com/en-us/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/vpn-deploy-ras

12. switch to lon-svr1 as adatum/administrator
13. lon-svr1 - enroll NPS server certificate
14. install NPS server 
    Install-WindowsFeature NPAS -IncludeManagementTools
15. configure NPS server detailed steps from https://docs.microsoft.com/en-us/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/vpn-deploy-nps

16. switch to lon-cl5
17. configure lon-cl5 to connect to "internet" (IP and hostname for vpn server)
18. configure certificate
19. configure connection profile using powershell




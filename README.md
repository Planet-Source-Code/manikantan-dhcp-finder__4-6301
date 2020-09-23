<div align="center">

## DHCP Finder


</div>

### Description

This Code WIll use cdonts.dll to mail the site owner

about the hit that was made to his site

1)Country From Which the Hit was Made

2)The Browser That Was Used

3)Time

4)Date
 
### More Info
 
Install cdonts.dll in the IIS

1)Country From Which the Hit was Made

2)The Browser That Was Used

3)Time

4)Date


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[manikantan](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/manikantan.md)
**Level**          |Intermediate
**User Rating**    |5.0 (10 globes from 2 users)
**Compatibility**  |ASP \(Active Server Pages\)
**Category**       |[Internet/ Browsers/ HTML](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/internet-browsers-html__4-9.md)
**World**          |[ASP / VbScript](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/asp-vbscript.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/manikantan-dhcp-finder__4-6301/archive/master.zip)





### Source Code

```
<%
'code by Manikantan
'Web Developer
'3rd Agenda
'Nungambakkam
'Chennai
'India
Dim RIPAddress
Dim UAgent
Dim strgetTime
RIPAddress = Request.ServerVariables("REMOTE_ADDR")
reg=split(RIPaddress,".")
'check for American regions
' Increase The Numbers into Subdomains to Find The Exact Location
if cint(reg(0))<=207 and cint(reg(0))>=204 then
region="North America or South America or Caribbean or Saharan Africa"
end if
if reg(0)="196" or reg(0)="198" or reg(0)="199" or reg(0)="200" or reg(0)="216" or reg(0)="208" or reg(0)="209" then
region="American regions Inclucding Caniberra and Saharian region"
end if
'Check for Asian Regions
'Increase the Check for Accuracy
if reg(0)="202" or reg(0)="203" or reg(0)="210" or reg(0)="211" or reg(0)="169" or reg(0)="61" or reg(0)="24" then
region="Asian pacific region like India,Afghan"
end if
if region <>"Asian pacific region like India,Afghan" then
if region<>"American regions Inclucding Caniberra and Saharian region" then
region="European Region,North Africa,Russian region"
end if
end if
UAgent = Request.ServerVariables("HTTP_USER_AGENT")
strgetTime = FormatDateTime(Now(),vbLongDate)
' you need cdonts.dll for this
' Anyother Mailer like abmailer.dll can be used instead
Dim myMail
Set myMail = Server.CreateObject("CDONTS.NewMail")
myMail.To = "youremail@home.com"
myMail.From = "admin@yourwebsite.com"
myMail.Subject = "You Have a Visitor " & strgettime
Body = "A visitor had visited your site:" & vbCrlf
Body = Body & "His DHCP Ip Was: " & RIPAddress & vbCrlf
Body = Body & "His Agent Was: " & UAgent & vbCrlf
Body = Body & "Date: " & strgetTime & vbCrlf
Body = Body & "The Hit was Approximately From" & vbcrlf
Body = Body & "<b>" & region & "</b>" & vbcrlf
myMail.Body = Body
myMail.Send
Set myMail = nothing
%>
```


!!! info ""

    ### Radius Ports

    | Radius Type            |  Default Radius Port |
    |:-----------------------|:---------------------|
    | Radius Authentication  |  1812                |
    | Radius Accounting      |  1813                |


!!! info ""

    ### Radius Codes

    | Radius Code 									| Description 																				                                             |
    |:----------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------|
    | Access-Reject (Code 3) 						|  Indicates that the user's credentials (username and/or password) are invalid 														 |
    | Access-Challenge (Code 11) 					|  Indicates that additional information is required from the user before access can be granted 										 |
    | NAS-Identification-Mismatch (Reason-Code 18) 	|  Indicates that the NAS (Network Access Server) identification in the request does not match the configured value on the RADIUS server |
    | Authentication-Failure (Reason-Code 19) 		|  Indicates that the authentication method used in the request is not supported or is not configured on the RADIUS server 				 |
    | Unknown-User-Name (Reason-Code 20) 			|  Indicates that the user's username is not found in the user database on the RADIUS server 											 |
    | User-Name-Ambiguity (Reason-Code 21) 			|  Indicates that the user's username is found multiple times in the user database on the RADIUS server 								 |
    | User-Account-Expired (Reason-Code 22) 		|  Indicates that the user's account has expired 																						 |
    | User-Account-Disabled (Reason-Code 23) 		|  Indicates that the user's account has been disabled																					 |
    | User-Account-Inactive (Reason-Code 24) 		|  Indicates that the user's account is inactive 																						 |
    | User-Account-Valid (Reason-Code 25) 			|  Indicates that the user's account is not valid 																						 |

!!! info ""

    ### Radius Wireshark Display Filter

    |Display Filter|Description|
    |:-|:-|
    |`radius` 			 | Show only the RADIUS traffic|
    |`radius.code == 1`  | Show only RADIUS Access-Request messages|
    |`radius.code == 2`  | Show only RADIUS Access-Accept messages|
    |`radius.code == 3`  | Show only RADIUS Access-Reject messages|
    |`radius.code == 4`  | Accounting Request|
    |`radius.time >= 2`  | Show only RADIUS response messages that take longer than two seconds from the request|
    |`radius.Acct_Status_Type == 1`  | Show only RADIUS Accounting-Request[start] messages|
    |`radius.Acct_Status_Type == 2`  | Show only RADIUS Accounting-Request[stop] messages|
    |`radius.code == 3 and radius.Reply_Message contains "password"` | Show only RADIUS Access-Reject messages that come with an Reply-Message attribute containing "password"|


!!! info ""

    ### Radius Wireshark Capture Filter

    |Capture Filter|Description|
    |:-|:-|
    |`udp port 1812` | Capture RADIUS authentication and configuration traffic over the assigned port (1812)|
    |`udp port 1813` | Capture RADIUS accounting traffic over the assigned port (1813)|
    |`udp port 1812 or udp port 1813` | Capture RADIUS authentication and configuration traffic, and RADIUS accounting traffic, over the assigned ports|

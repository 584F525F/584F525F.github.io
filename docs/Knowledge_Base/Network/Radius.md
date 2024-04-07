
---

| Radius Type            |  Default Radius Port |
|:-----------------------|:---------------------|
| Radius Authentication  |  1812                |
| Radius Accounting      |  1813                |

---

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

---

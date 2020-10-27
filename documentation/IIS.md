# Application Host Configuration Test
The `applicationhostconfig_test` evaluates global configuration settings that are used by the Windows Process Activation Service (WAS) in Internet Information Services (IIS). This element defines many of the server-level configuration settings in the IIS 7 ApplicationHost.config file. Of significant importance, the Application Host Configuration Item contains the configuration settings for the  Application Pools and Sites, which respectively define the collection of application pools and Web sites on an IIS server.  Note: Unlike the settings that are found in system.webServer, settings in the Application Host Configuration Item element cannot be delegated.

## Example
```
<applicationhostconfig_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis" check="all" check_existence="any_exist" comment="Ensure 'allow_unlisted_isapis' is 'equals' to 'false'" id="oval:org.cisecurity.benchmarks.microsoft_iis_10:tst:465681" version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.microsoft_iis_10:obj:465681"></object>
    <state state_ref="oval:org.cisecurity.benchmarks.microsoft_iis_10:ste:465681"></state>
</applicationhostconfig_test>
```

# Application Host Configuration Object
The `applicationhostconfig_object` element is used by Application Host Configuration Test to define those objects to evaluate based on a specified state. There is actually only one object relating to Application Host Configuration and this is the system as a whole. Therefore, there are no child entities defined. Any OVAL Test written to check the Application Host Configuration will reference the same applicationhostconfig_object which is basically an empty object element.

## Example
```
<applicationhostconfig_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis" comment="Ensure 'allow_unlisted_isapis' is 'equals' to 'false'" id="oval:org.cisecurity.benchmarks.microsoft_iis_10:obj:465681" version="1">
</applicationhostconfig_object>
```

# Application Host Configuration State
The `applicationhostconfig_state` evaluates global configuration settings that are used by the Windows Process Activation Service (WAS) in Internet Information Services (IIS). This element defines many of the server-level configuration settings in the IIS 7 ApplicationHost.config file.Of significant importance, the Application Host Configuration Item contains the configuration settings for the Application Pools and Sites, which respectively define the collection of application pools and Web sites on an IIS server.  Note: Unlike the settings that are found in system.webServer, settings in the Application Host Configuration Item element cannot be delegated.

## State Elements
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| allow_unlisted_isapis | EntityStateBoolType | Indicates whether or not users can copy unauthorized ISAPI binaries to the web server and run them |
| allow_unlisted_cgis | EntityStateBoolType | Indicates whether or not users can copy unauthorized CGI binaries to the web server and run them |
| advanced_logging_enabled | EntityStateBoolType | Indicates whether or not IIS advanced logging is enabled. |
| default_web_log_directory | EntityStateStringType | Indicates the physical path to the default IIS Web Logs |

## Example
```
<applicationhostconfig_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis" comment="Ensure 'allow_unlisted_isapis' is 'equals' to 'false'" id="oval:org.cisecurity.benchmarks.microsoft_iis_10:ste:465681" version="1">
    <allow_unlisted_isapis datatype="boolean" operation="equals" var_ref="oval:org.cisecurity.benchmarks.microsoft_iis_10:var:465681"></allow_unlisted_isapis>
</applicationhostconfig_state>
```

# Application Host Configuration Item
A `applicationhostconfig_item` contains global configuration settings that are used by the Windows Process Activation Service (WAS) in Internet Information Services (IIS). This element defines many of the server-level configuration settings in the IIS 7 ApplicationHost.config file. Of significant importance, the Application Host Configuration Item contains the configuration settings for the Application Pools and Sites, which respectively define the collection of application pools and Web sites on an IIS server.  Note: Unlike the settings that are found in system.webServer, settings in the Application Host Configuration Item element cannot be delegated.

## Item Elements
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| allow_unlisted_isapis | EntityItemBoolType | Indicates whether or not users can copy unauthorized ISAPI binaries to the web server and run them |
| allow_unlisted_cgis | EntityItemBoolType | Indicates whether or not users can copy unauthorized CGI binaries to the web server and run them |
| advanced_logging_enabled | EntityItemBoolType | Indicates whether or not IIS advanced logging is enabled. |
| default_web_log_directory | EntityItemStringType | Indicates the physical path to the default IIS Web Logs |


# Web Server Configuration Test
The `webconfig_test` evaluates many of the site-level and application-level configuration settings for Internet Information Services (IIS) 7 and above in the ApplicationHost.config file, and contains configuration elements that define the settings used by the Web server engine and modules.


## Example
```
<webconfig_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis" check="all" check_existence="at_least_one_exists" comment="Ensure 'directory_browse_enabled' is 'equals' to 'false'" id="oval:org.cisecurity.benchmarks.microsoft_iis_10:tst:465655" version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.microsoft_iis_10:obj:465655"></object>
    <state state_ref="oval:org.cisecurity.benchmarks.microsoft_iis_10:ste:465655"></state>
</webconfig_test>
```

# Web Server Configuration Object
The `webconfig_object` determines which Sites, Applications, and/or Virtual Directories for which to collect configuration characteristics.

## Object Elements
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| site_name | EntityObjectStringType | The name of the IIS managed Site |
| application_name | EntityObjectStringType | The name of the application. |
| virtual_directory_name | EntityObjectStringType | The name of a virtual directory to collect. |

## Example
```
<webconfig_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis" comment="Ensure 'directory_browse_enabled' is 'equals' to 'false'" id="oval:org.cisecurity.benchmarks.microsoft_iis_10:obj:465655" version="1">
    <site_name operation="pattern match">.*</site_name>
    <application_name operation="pattern match">.*</application_name>
    <virtual_directory_name operation="pattern match">.*</virtual_directory_name>
</webconfig_object>
```


# Web Server Configuration State
The `webconfig_state` evaluates many of the site-level and application-level configuration settings for Internet Information Services (IIS) 7 and above in the ApplicationHost.config file, and contains configuration elements that define the settings used by the Web server engine and modules.

## State Elements
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| site_name | EntityStateStringType | The name of the IIS |
| application_name | EntityStateStringType | The name of the application.  This value will be empty for site-level configuration information, as well as for virtual directories which are non-application related. |
| virtual_directory_name | EntityStateStringType | The name of the virtual directory.  This value will be empty for site-level configuration information, as well as for application-related configurations. |
| physical_path | EntityStateStringType | From a site or directory's configuration page, click Basic Settings.  See Physical Path field |
| directory_browse_enabled | EntityStateBoolType | Is directory browsing enabled? |
| anonymous_authentication_enabled | EntityStateBoolType | Is anonymous authentication enabled? |
| anonymous_authentication_username | EntityStateStringType | Specific username tied to the anonymous user identity |
| dynamic_ip_concurrent_enabled | EntityStateBoolType | Is 'Deny IP Address based on the number of concurrent requests' enabled?  This element is applicable only to IIS 8/8.5 |
| dynamic_ip_max_concurrent | EntityStateIntType | Maximum number of concurrent requests.  This element is applicable only to IIS 8/8.5 |
| http_error_mode | EntityStateHttpErrorModeType | Indicates how detailed error messages are displayed to users |
| request_limits_max_content_length | EntityStateFloatType | Maximum size, in bytes, of the HTTP request |
| request_limits_max_url | EntityStateIntType | Maximum length, in bytes, in which a requested URL can be (excluding query string) in order for IIS to accept. |
| request_limits_max_query | EntityStateIntType | The upper limit on the length of the query string that the configured IIS server will allow for websites or applications. |
| request_filter_allow_high_bit | EntityStateBoolType | Indicates whether or not a request will be accepted or denied if non-ASCII characters are present in the URL |
| request_filter_allow_double_escaping | EntityStateBoolType | Indicates whether or not double-encoded requests are allowed |
| request_filter_allow_unlisted_extensions | EntityStateBoolType | Indicates whether or not requests for resources containing unlisted file extensions are allowed. |
| handler_access_policy | EntityStateStringType | Indicates the allowed permissions for handler mappings |
| request_filter_allow_trace | EntityStateBoolType | Indicates whether or not to allow usage of HTTP TRACE methods |

## Example
```
<webconfig_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis" comment="Ensure 'directory_browse_enabled' is 'equals' to 'false'" id="oval:org.cisecurity.benchmarks.microsoft_iis_10:ste:465655" version="1">
    <directory_browse_enabled datatype="boolean" operation="equals" var_ref="oval:org.cisecurity.benchmarks.microsoft_iis_10:var:465655"></directory_browse_enabled>
</webconfig_state>
```

# Web Server Configuration Item
The `webconfig_item` specifies many of the site-level and application-level configuration settings for Internet Information Services (IIS) 7 and above in the ApplicationHost.config file, and contains configuration elements that define the settings used by the Web server engine and modules.

## Item Elements
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| site_name | EntityItemStringType | The name of the IIS |
| application_name | EntityItemStringType | The name of the application.  This value will be empty for site-level configuration information, as well as for virtual directories which are non-application related. |
| virtual_directory_name | EntityItemStringType | The name of the virtual directory.  This value will be empty for site-level configuration information, as well as for application-related configurations. |
| physical_path | EntityItemStringType | From a site or directory's configuration page, click Basic Settings.  See Physical Path field |
| directory_browse_enabled | EntityItemBoolType | Is directory browsing enabled? |
| anonymous_authentication_enabled | EntityItemBoolType | Is anonymous authentication enabled? |
| anonymous_authentication_username | EntityItemStringType | Specific username tied to the anonymous user identity |
| dynamic_ip_concurrent_enabled | EntityItemBoolType | Is 'Deny IP Address based on the number of concurrent requests' enabled?  This element is applicable only to IIS 8/8.5 |
| dynamic_ip_max_concurrent | EntityItemIntType | Maximum number of concurrent requests.  This element is applicable only to IIS 8/8.5 |
| http_error_mode | EntityItemHttpErrorModeType | Indicates how detailed error messages are displayed to users |
| request_limits_max_content_length | EntityItemFloatType | Maximum size, in bytes, of the HTTP request |
| request_limits_max_url | EntityItemIntType | Maximum length, in bytes, in which a requested URL can be (excluding query string) in order for IIS to accept. |
| request_limits_max_query | EntityItemIntType | The upper limit on the length of the query string that the configured IIS server will allow for websites or applications. |
| request_filter_allow_high_bit | EntityItemBoolType | Indicates whether or not a request will be accepted or denied if non-ASCII characters are present in the URL |
| request_filter_allow_double_escaping | EntityItemBoolType | Indicates whether or not double-encoded requests are allowed |
| request_filter_allow_unlisted_extensions | EntityItemBoolType | Indicates whether or not requests for resources containing unlisted file extensions are allowed. |
| handler_access_policy | EntityItemStringType | Indicates the allowed permissions for handler mappings |
| request_filter_allow_trace | EntityItemBoolType | Indicates whether or not to allow usage of HTTP TRACE methods |



# Application Pool Test
An `applicationpool_test` contains configuration settings for all application pools running on your Internet Information Services (IIS) 7 or later server. An application pool defines a group of one or more worker processes, configured with common settings that serve requests to one or more applications that are assigned to that application pool. Because application pools allow a set of Web applications to share one or more similarly configured worker processes, they provide a convenient way to isolate a set of Web applications from other Web applications on the server computer. Process boundaries separate each worker process; therefore, application problems in one application pool do not affect Web sites or applications in other application pools. Application pools significantly increase both the reliability and manageability of your Web infrastructure.

## Example
```
<applicationpool_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis" check="all" check_existence="at_least_one_exists" comment="Ensure 'identity_type' is 'case insensitive equals' to 'ApplicationPoolIdentity'" id="oval:org.cisecurity.benchmarks.microsoft_iis_10:tst:465656" version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.microsoft_iis_10:obj:465656"></object>
    <state state_ref="oval:org.cisecurity.benchmarks.microsoft_iis_10:ste:465656"></state>
</applicationpool_test>
```

# Application Pool Object
The `applicationpool_object` defines which application pools to collect for evaluation.  
Each object extends the standard ObjectType as defined in the oval-definitions-schema and one should refer to the ObjectType 
description for more information.  The common set element allows complex objects to be created using filters and set logic.  
Again, please refer to the description of the set element in the oval-definitions-schema.

## Object Elements
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| applicationpool_name | EntityStateStringType | The name of the application pool |

## Example
```
<applicationpool_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis" comment="Ensure 'identity_type' is 'case insensitive equals' to 'ApplicationPoolIdentity'" id="oval:org.cisecurity.benchmarks.microsoft_iis_10:obj:465656" version="1">
    <applicationpool_name operation="pattern match">.+</applicationpool_name>
</applicationpool_object>
```

# Application Pool State
An `applicationpool_state` evaluates expected configuration settings for all application pools running on your Internet Information Services (IIS) 7 or later server. An application pool defines a group of one or more worker processes, configured with common settings that serve requests to one or more applications that are assigned to that application pool. Because application pools allow a set of Web applications to share one or more similarly configured worker processes, they provide a convenient way to isolate a set 
of Web applications from other Web applications on the server computer. Process boundaries separate each worker process; therefore, application problems in one application pool do not affect Web sites or applications in other application pools. Application pools significantly increase both the reliability and manageability of your Web infrastructure.

## State Elements
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| applicationpool_name | EntityStateStringType | The name of the application pool |
| identity_type | EntityStateStringType | The identity for which the application pool is executed |
| application_count | EntityStateIntType | The number of applications to which this application pool is associated |

## Example
```
<applicationpool_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis" comment="Ensure 'identity_type' is 'case insensitive equals' to 'ApplicationPoolIdentity'" id="oval:org.cisecurity.benchmarks.microsoft_iis_10:ste:465656" version="1">
    <identity_type datatype="string" operation="case insensitive equals" var_ref="oval:org.cisecurity.benchmarks.microsoft_iis_10:var:465656"></identity_type>
</applicationpool_state>
```

# Application Pool Item
An `applicationpool_item` contains configuration settings for all application pools running on your Internet Information Services (IIS) 7 or later server. An application pool defines a group of one or more worker processes, configured with common settings that serve requests to one or more applications that are assigned to that application pool. Because application pools allow a set of Web applications to share one or more similarly configured worker processes, they provide a convenient way to isolate a set of Web applications from other Web applications on the server computer. Process boundaries separate each worker process; therefore, application problems in one application pool do not affect Web sites or applications in other application pools. Application pools significantly increase both the reliability and manageability of your Web infrastructure.

## Item Elements
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| applicationpool_name | EntityItemStringType | The name of the application pool |
| identity_type | EntityItemStringType | The identity for which the application pool is executed |
| application_count | EntityItemIntType | The number of applications to which this application pool is associated |


# Site Bindings Test
The `bindings_test` is used to determine the bindings for sites managed in IIS, including http and https bindings.  It extends the standard TestType as defined in the oval-definitions-schema and one should refer to the TestType description for more information. The required object element references a vmhost_modules_object and the optional state element specifies the data to check.


## Example
```
<bindings_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis" check="all" check_existence="any_exist" comment="Ensure host headers are on all sites" id="oval:org.cisecurity.benchmarks.microsoft_iis_10:tst:465654" version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.microsoft_iis_10:obj:465654"></object>
    <state state_ref="oval:org.cisecurity.benchmarks.microsoft_iis_10:ste:465654"></state>
</bindings_test>
```

# Site Bindings Object
The `bindings_object` element is used by the bindings_test to define the object to be evaluated.  Each object extends the standard ObjectType as defined in the oval-definitions-schema and one should refer to the ObjectType description for more information.  The common set element allows complex objects to be created using filters and set logic.  Again, please refer to the description of the set element in the oval-definitions-schema.

## Object Elements
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| site_name | EntityObjectStringType | The name of the site for which to collect the bindings. |


## Example
```
<bindings_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis" comment="Ensure host headers are on all sites" id="oval:org.cisecurity.benchmarks.microsoft_iis_10:obj:465654" version="1">
    <site_name operation="pattern match">.*</site_name>
</bindings_object>
```

# Site Bindings State
The `bindings_state` allows you to configure the information required for requests to communicate with a Web site.  You can configure binding information when you create a Web site, or you can edit the binding information after you create the site. Binding information includes the protocol that clients use to communicate with the site, the site's IP address, the port number, and a host header.

## State Elements
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| site_name | EntityStateStringType | The name of the site |
| protocol | EntityStateStringType | protocol for the binding. |
| ip_address | EntityStateStringType | IP Address of the site binding |
| port | EntityStateIntType | The port number of the site binding. |
| host_header | EntityStateStringType | Host name information for the site binding. |
| ssl_flags | EntityStateBindingSSLFlagsType | Flags associated with the SSL settings in the site binding.  This element is applicable only to IIS 8/8.5 |

## Example
```
<bindings_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis" comment="Ensure host headers are on all sites" id="oval:org.cisecurity.benchmarks.microsoft_iis_10:ste:465654" version="1">
    <host_header datatype="string" operation="pattern match" var_ref="oval:org.cisecurity.benchmarks.microsoft_iis_10:var:465654"></host_header>
</bindings_state>
```

# Site Bindings Item
The `bindings_item` element allows you to configure the information required for requests to communicate with a Web site.  You can configure binding information when you create a Web site, or you can edit the binding information after you create the site. Binding information includes the protocol that clients use to communicate with the site, the site's IP address, the port number, and a host header.

## Item Elements
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| site_name | EntityItemStringType | The name of the site |
| protocol | EntityItemStringType | protocol for the binding. |
| ip_address | EntityItemStringType | IP Address of the site binding |
| port | EntityItemIntType | The port number of the site binding. |
| host_header | EntityItemStringType | Host name information for the site binding. |
| ssl_flags | EntityItemBindingSSLFlagsType | Flags associated with the SSL settings in the site binding.  This element is applicable only to IIS 8/8.5 |


# Site SystemWeb Test
The `systemweb_test` is used to determine certain aspects of an IIS Site's configuration.  It extends the standard TestType as defined in the oval-definitions-schema and one should refer to the TestType description for more information. The required object element references a systemweb_object and the optional state element specifies the data to check.

## Example
```
<systemweb_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis" check="all" check_existence="any_exist" comment="Ensure 'forms_require_ssl' is 'equals' to 'true'" id="oval:org.cisecurity.benchmarks.microsoft_iis_10:tst:465659" version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.microsoft_iis_10:obj:465659"></object>
    <state state_ref="oval:org.cisecurity.benchmarks.microsoft_iis_10:ste:465659"></state>
</systemweb_test>
```

# Site SystemWeb Object
The `systemweb_object` element is used by the systemweb_test to define the object to be evaluated.  Each object extends the standard ObjectType as defined in the oval-definitions-schema and one should refer to the ObjectType description for more information.  The common set element allows complex objects to be created using filters and set logic.  Again, please refer to the description of the set element in the oval-definitions-schema.

## Object Elements 
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| site_name | EntityObjectStringType | The name of the site from which to collect information. |
| application_name | EntityObjectStringType | The name of an application to collect. |
| virtual_directory_name | EntityObjectStringType | The name of a virtual directory to collect. |

## Example
```
<systemweb_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis" comment="Ensure 'forms_require_ssl' is 'equals' to 'true'" id="oval:org.cisecurity.benchmarks.microsoft_iis_10:obj:465659" version="1">
    <site_name operation="pattern match">.*</site_name>
    <application_name operation="pattern match">.*</application_name>
    <virtual_directory_name operation="pattern match">.*</virtual_directory_name>
    <filter xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5" action="include">oval:org.cisecurity.benchmarks.microsoft_iis_10:ste:465659</filter>
</systemweb_object>
```

# Site SystemWeb State
The `systemweb_state` element defines the information that can be used to evaluate the specified IIS site configuration information.

## State Elements
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| site_name | EntityStateStringType | The name of the site from which to collect informatio |
| application_name | EntityStateStringType | application path (empty for server-level config) |
| virtual_directory_name | EntityStateStringType | virtual directory name (empty for server-level config) |
| authentication_mode | EntityStateAuthenticationModeType | Specifies the default authentication mode for an application |
| forms_require_ssl | EntityStateBoolType | Indicates whether the site requires SSL |
| forms_cookieless | EntityStateCookielessType | Indicates how forms authentication uses cookies |
| forms_protection | EntityStateProtectionType | The cookie protection mode defines the protection Forms Authentication cookies will be given within a configured application |
| forms_credential_format | EntityStateCredentialFormatType | Indicates how authentication credentials are protected |
| retail | EntityStateBoolType | Indicates if the site utilizes the retail deployment method |
| debug | EntityStateBoolType | Indicates if the site's debug information is enabled |
| custom_errors | EntityStateCustomErrorsType | Specifies how custom error messages are displayed to users |
| session_state_cookieless | EntityStateCookielessType | Indicates how the session cookies are enabled |
| http_only_cookies | EntityStateBoolType | Indicates to the user agent whether or not the cookie is accessible by client-side script |
| trace_enabled | EntityStateBoolType | Indicates if the ASP.NET code tracing service is enabled |
| machine_key_validation | EntityStateMachineKeyValidationType | Indicates the algorithm and keys that ASP.NET will use for encryption< |
| trust_level | EntityStateTrustLevelType | Specifies the trust level under which the application will run. |
| http_error_mode | EntityStateHttpErrorModeType | Indicates how detailed error messages are displayed to users |



## Example
```
<systemweb_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis" comment="Ensure 'forms_require_ssl' is 'equals' to 'true'" id="oval:org.cisecurity.benchmarks.microsoft_iis_10:ste:465659" version="1">
    <forms_require_ssl datatype="boolean" operation="equals" var_ref="oval:org.cisecurity.benchmarks.microsoft_iis_10:var:465659"></forms_require_ssl>
</systemweb_state>
```

# Site SystemWeb Item
The `systemweb_item` configuration item collects site, application, and virtual directory information contained in the respective systemWeb configuration.

## Item Elements
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| site_name | EntityItemStringType | The name of the site from which to collect informatio |
| application_name | EntityItemStringType | application path (empty for server-level config) |
| virtual_directory_name | EntityItemStringType | virtual directory name (empty for server-level config) |
| authentication_mode | EntityItemAuthenticationModeType | Specifies the default authentication mode for an application |
| forms_require_ssl | EntityItemBoolType | Indicates whether the site requires SSL |
| forms_cookieless | EntityItemCookielessType | Indicates how forms authentication uses cookies |
| forms_protection | EntityItemProtectionType | The cookie protection mode defines the protection Forms Authentication cookies will be given within a configured application |
| forms_credential_format | EntityItemCredentialFormatType | Indicates how authentication credentials are protected |
| retail | EntityItemBoolType | Indicates if the site utilizes the retail deployment method |
| debug | EntityItemBoolType | Indicates if the site's debug information is enabled |
| custom_errors | EntityItemCustomErrorsType | Specifies how custom error messages are displayed to users |
| session_Item_cookieless | EntityItemCookielessType | Indicates how the session cookies are enabled |
| http_only_cookies | EntityItemBoolType | Indicates to the user agent whether or not the cookie is accessible by client-side script |
| trace_enabled | EntityItemBoolType | Indicates if the ASP.NET code tracing service is enabled |
| machine_key_validation | EntityItemMachineKeyValidationType | Indicates the algorithm and keys that ASP.NET will use for encryption< |
| trust_level | EntityItemTrustLevelType | Specifies the trust level under which the application will run. |
| http_error_mode | EntityItemHttpErrorModeType | Indicates how detailed error messages are displayed to users |


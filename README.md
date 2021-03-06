# **YJSoapEngine v1.1.1** #

YJSoapEngine is a class designed to simplify the implementation of a SOAP Web Service for iPhone, iPad. YJSoapEngine can be used to serialize custom objects for Soap Requests.

# ARC Compatibility #

As of version 1.0.0, YJSoapEngine requires ARC. If you wish to use YJSoapEngine in a non-ARC project, just add the -fobjc-arc compiler flag to the YJSoapEngine.m class. To do this, go to the Build Phases tab in your target settings, open the Compile Sources group, double-click YJSoapEngine.m in the list and type -fobjc-arc into the popover.

**Note:** XmlParser.m,OrderedDictionary.m and GDataXMLNode.m is non - ARC. If used in ARC project, just add the **-fno-objc-arc** flag to these classes. To do this, go to the Build Phases tab in your target settings, open the Compile Sources group, double-click XmlParser.m and GDataXMLNode.m and  in the list and type -**fno-objc-arc** into the popover.

# Installation #

# Using CocoaPods #

Just add the following to your pod file

```pod 'YJSoapEngine' ```

# Lame Installation #

To use the YJSoapEngine class in an app, just drag the files in the YJSoapEngine folder and add them in your project.

Add **/usr/include/libxml2** in Header Search Paths in Build Settings.
Also add the **-lxml2** in Other Linker Flags in Build Settings.
# How to use #

```
@property BOOL actionNamespaceSlash;
```
Sets whether the Envelope Namespace is specified in the SoapAction before the last slash.


```
@property SoapAuthType authenticationMethod;
```
Sets the soap authentication type.

```
@property NSString *username, *password;
```
Sets the username and password for authentication if authenticationMethod is SoapAuthBasic
```
- (void)setObject:(id)object andTag:(NSString *)tag andNamespace:(NSString *)nameSpace;
```
This method is used to set a custom object in the SOAP Request. This method serializes in the custom object. Tag parameter is optional to set the tag name of the object. Namespace parameter is used to set the namespace of the object.

```
- (void)setInteger:(int)value andTag:(NSString *)tag;
```

This method is used to set an Integer value in the SOAP Request. Tag is used to specify the tag name to be used.

```
- (void)setFloat:(float)value andTag:(NSString *)tag;
```

This method is used to set a Float value in the SOAP Request. Tag is used to specify the tag name to be used.

```
- (void)setString:(NSString *)value andTag:(NSString *)tag;
```

This method is used to set a String value in the SOAP Request. Tag is used to specify the tag name to be used.

```
- (void)requestURL:(NSString *)reqURL withSoapAction:(NSString *)soapAction;
```

This method is used to send the SOAP Request to the specified URL and the specified SOAP Action.

# Delegate Method #

```
- (void)YJSoapEngine:(YJSoapEngine *)soapEngine didRecieveData:(NSString *)data inDictionary:(NSDictionary *)dataDictionary;
```
Required Method. This method is called when the SOAPResponse is received.

```
- (void)YJSoapEngine:(YJSoapEngine *)YJSoapEngine didRecieveError:error inDictionary:(NSDictionary *)errorDictionary;
```
Required Method. This method is called when the SOAPResponse receives an error.

# ThePBone.WbXml2
This library is a managed wrapper around libwbxml (aka libwbxml2) available at: https://github.com/libwbxml/libwbxml

This library includes a precompiled version of the C++ library for Windows. For macOS and Linux, you need to bring your own compiled binary files. Name the binary libwbxml2.so (Linux) or `libwbxml2.dylib` (macOS) and bundle it within the working directory of your application or in a directory specified in the global `PATH` system environment variable.

## Examples

### Convert Wbxml to Xml

This example uses sample wbxml content from an OMA-DM transaction embedded as a Base64 string.
```c#
var encodedWbxmlContent =
    "AgAAaoE5LS8vU1lOQ01MLy9EVEQgU3luY01MIDEuMi8vRU4AMS4yAERNLzEuMgAwMmI0ADUAVFdJRDo2NDAzN0" +
    "YyRTJCM0EAaHR0cHM6Ly9jZm90YTEub3Nwc2VydmVyLm5ldC92MS9kZXZpY2UvbWFnaWNzeW5jL21kbT9zaWQ9" +
    "MGZiYTMyYmYwMmE4NGM0OGIxNTI3NzI4MzMzMWNjYTAANTEyMAAxMDQ4NTc2ADEAMABTeW5jSGRyADIwMABtbH" +
    "GDHgFygyIBZYMpAVuDLgFuV4MwAVaDMAEBZ1eDQgEBYYNCAVoAAUyDgRwBVYOBIQEBAQAAa2lLg4EpAVyDLgFM" +
    "g4ErAUqDgS0Bb4NCAWiDMAFPg4E1AQESAQE="; 

var parser = new WbXmlParser()
{
    Charset = WBXMLCharsetMIBEnum.WBXML_CHARSET_UTF_8,
    WbXmlLanguage = WBXMLLanguage.WBXML_LANG_SYNCML_SYNCML12,
    XmlGenerationType = WBXMLGenXMLType.WBXML_GEN_XML_INDENT,
    IndentSpaces = 3
};

var xml = parser.WriteXmlString(Convert.FromBase64String(encodedWbxmlContent));
Console.Write(xml);
```

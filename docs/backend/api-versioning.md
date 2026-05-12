# API Versioning

## Strategies

### Attribute-controlled versioning

- URL Path Versioning
    - Example url: [https://localhost:7142/**v0.1**/persons](https://localhost:7142/v0.1/persons) 
        - ✅Simple and explicit
        - ⚠️ Breaks REST principles
        - ⚠️ Increased coupling between client and server
- Query String Versioning
    - Example url: [https://localhost:7142/persons?**api-version=0.1**](https://localhost:7142/persons?api-version=0.1) 
        - ✅ Keeps URI structure clean
        - ⚠️ Less visible to clients  
- Header Versioning
    - Example url: [https://localhost:7142/persons](https://localhost:7142/persons) with **Header api-version: 1.0**  
        For the sake of completeness, this also includes Capability headers
        - ✅ Aligns with REST best practices
        - ⚠️Harder for clients to discover and test
        - ⚠️Requires custom middleware or configuration  
- Media Type Versioning
    - Example url: [https://localhost:7142/persons](https://localhost:7142/persons) with **Content-Type application/ApplicationInfo.v0.1+json**
        - ✅Decouples versioning from url
        - ✅Provides backward compatibility, as long as the media type is still supported
        - ⚠️ More complex to document and implement  
    
### Physical Separation

- New Resource variant
    - Introduce a new resource alongside the old one (e.g., /persons and /persons-extended)
        - ✅No formal versioning
        - ✅Allows for gradual migration
        - ✅Clean Separation of concerns
        - ⚠️ Higher complexity  
- New Service Endpoint
    - Deploy a whole new application or service with a new domain or base path.
        - ✅Full isolation of versions
        - ✅Clean separation of concerns
        - ⚠️ High operational overhead
     
## Implementatio (.net)

This official dotnet nuget enables the implementation of a nice api-versioning: [https://github.com/dotnet/aspnet-api-versioning](https://github.com/dotnet/aspnet-api-versioning) with good documentation [https://github.com/dotnet/aspnet-api-versioning/wiki](https://github.com/dotnet/aspnet-api-versioning/wiki)

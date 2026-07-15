![MagicMapper.Data]
================================

#### The data extensions to MagicMapper, IDataReader support
#### This project is a community-maintained fork of AutoMapper.Data adapted to work with MagicMapper. It aims to remain API-compatible while replacing the AutoMapper dependency with MagicMapper.

## Installation

```bash
dotnet add package MagicMapper.Data
```

or

```xml
<PackageReference Include="MagicMapper.Data" Version="x.x.x" />
```

##### Install via initialization:

```csharp
var mapper = new Mapper(cfg => {
   cfg.AddDataReaderMapping();
   cfg.CreateMap<IDataRecord, MyDto>();
   cfg.CreateMap<IDataRecord, MyOtherDto>();
   // Other config
});

// or with the MagicMapper dependency injection package:

services.AddAutoMapper(typeof(Startup), cfg => {
	cfg.AddDataReaderMapping();
});
```

You will need to configure maps for each `IDataRecord` DTO mapping.

##### Using `Profile`:

There are several ways to configure mapping with an instance of `Profile`:

- Create an instance of Profile, call the `Profile.AddDataRecordMember` extension method on it, and add it to the configuration.
- Call `AddMemberConfiguration().AddMember<DataRecordMemberConfiguration>()` on the instance.
- Call the `IMapperConfigurationExpression.AddDataReaderProfile` extension method.

## Compatibility

MagicMapper.Data is API-compatible with AutoMapper.Data and is intended as a drop-in replacement for applications using MagicMapper.

Only the underlying mapper dependency has changed.
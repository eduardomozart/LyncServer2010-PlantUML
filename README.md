# Lync Server 2010 icons for PlantUML

It uses the topology icons available at [Lync Server 2010 Visio Stencil](https://www.microsoft.com/en-us/download/details.aspx?id=20891) (LyncServer2010VisioStencil.vss) which provides some Microsoft icons of Windows Server 2008' era.

PlantUML doesn't handle PNG alpha (transparent images), so I moved the original PNG files to the ``alpha/`` subfolder for anyone interested on them.

Also the PNG rendering was huge, so I resize their width/height by 96px (width).

The VSS stencil to SVG/PNG conversion process has been documented [here](https://translate.google.com/translate?sl=pt&tl=en&hl=pt-BR&u=https://eduardomozartdeoliveira.wordpress.com/2023/01/30/instalacao-do-libvisio2svg-no-macos/).

## Samples

### Certificate Authority (AD CS)

![Basic Usage - Certificate Authority](https://www.plantuml.com/plantuml/png/fPBTJjnE3CNlvoaC-b_yUy4c5BMLK8jO5bMjH2i4_U02gN8dtiHYueaypb90F4oVfI_MR2BsO-bDwLwjZy_vUJoPmsIerjR19O-1O3VRS-cAfK756WgQOXliRHJxY3N1EmepClRe0aqDB89oMHaKhEIDepYtrMLO24vkn9zsNAZCchIVPOhNevAjQh-tYTHtI18R-LXdLBIeHQpZBQfby-0vwOpqURwRxvm65FlyuIIhaSLjiVZG5alyXlqB9uxdHk8vPCsyFo4rdh97ez5S-3V4jy7tLD89DXQR8UqgxgB9I2dQJKDkvTxl77I_iMgydiGG5Ou2-gjUF1u-oIVwOUF0fTGa1fx4IFl-KMSiDRPI3Ccl5HlrdLHX4QzPIfXYI8DsDXXLI64txwMYOTZBStU_UY0bRoXb8BZxunHJbDHPIMpeHor87_Sww1Ar_Vg_nrTxrx_3D_derOlxWqiPJq2HRo_b_xCO3IRZPzk02UR5PFptB1OZhQdWNp-LiQE-Vn3GQ45V5PyoXMfEAMhFJwbbAPVeeTwa3WzZGNhPauuvDJ6nyIp2HPy-fXbxkd1ks1zsTWus3xjU3ex5pCM_kVv0WtrOMsjj7tT8KhHr-0q0)

```csharp
@startuml
scale 1/3
skinparam defaultFontName Helvetica
left to right direction

!define LyncPuml https://raw.githubusercontent.com/eduardomozart/LyncServer2010-PlantUML/main
!include LyncPuml/LyncServer2010VisioStencil/puml/Certificate.puml
!include LyncPuml/LyncServer2010VisioStencil/puml/Certificate_Server.puml
!include LyncPuml/LyncServer2010VisioStencil/puml/Laptop.puml

hide stereotype

skinparam {
    ArrowColor Black
    DefaultTextAlignment center
    BackgroundColor White
    shadowing false
    RoundCorner 10
    dpi 300
}

skinparam rectangle {
    BackgroundColor transparent
    BorderColor transparent
}

rectangle "<$Certificate_Server{scale=0.75}>\nAC raiz\n(Root CA)" as RootCA
rectangle "<$Certificate_Server{scale=0.75}>\nAC intermediária\n(Intermediate CA)" as IntermediateCA
rectangle "<$Certificate_Server{scale=0.75}>\nAC emissora\n(Issuing CA)" as IssuingCA
rectangle "<$Laptop{scale=0.65}>\nDispositivo X" as DeviceX

RootCA --> IntermediateCA
IntermediateCA --> IssuingCA
IssuingCA --> DeviceX : <$Certificate{scale=0.75}>
@enduml
```

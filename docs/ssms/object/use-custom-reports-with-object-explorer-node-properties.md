---
title: Использование пользовательских отчетов совместно со свойствами узлов обозревателя объектов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: c7b84355-71ba-402d-85af-23826f18b7da
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: a469266b493e1da741738984c1f99b2c1f755699
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65095687"
---
# <a name="use-custom-reports-with-object-explorer-node-properties"></a>Использование пользовательских отчетов совместно со свойствами узлов обозревателя объектов
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Пользовательские отчеты могут выполняться в контексте выбранного узла обозревателя объектов, если они ссылаются на параметры отчета этого узла. Это позволяет пользовательскому отчету использовать текущий контекст, например текущей базы данных либо объекта базы данных или сервера.  
  
## <a name="object-explorer-node-report-parameters"></a>Параметры отчета узла обозревателя объектов  
  
|Имя параметра|Тип данных|  
|------------------|-------------|  
|**ObjectName**|**Строковые значения**|  
|**ObjectTypeName**|**String**|  
|**Фильтруемый**|**Логическое значение**|  
|**ServerName**|**String**|  
|**FontName**|**String**|  
|**DatabaseName**|**String**|  
  
## <a name="object-explorer-node-report-parameters-example"></a>Пример параметров отчета узла обозревателя объектов  
Пример запускается с помощью следующей процедуры.  
  
**Просмотр значений параметров отчета для узла в обозревателе объектов**  
  
1.  Скопируйте следующий образец кода в новый текстовый файл и присвойте ему имя с расширением RDL.  
  
2.  Скопируйте файл отчета в папку, созданную на сервере баз данных для пользовательских отчетов.  
  
3.  В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]щелкните узел в обозревателе объектов, укажите **Отчеты**и выберите "Пользовательские отчеты". В диалоговом окне **Открытие файла** перейдите в папку пользовательских отчетов, выберите файл отчета и нажмите кнопку **Открыть**.  
  
    При первом открытии пользовательского отчета из узла в обозревателе этот отчет добавляется к списку недавно использовавшихся **пользовательских отчетов** в контекстном меню этого узла. При первом открытии стандартного отчета он также отобразится в списке недавно использовавшихся **пользовательских отчетов**. Если удалить пользовательский отчет, при следующем выборе этого элемента появится запрос на удаление его из списка недавно использовавшихся отчетов.  
  
    1.  Чтобы изменить количество файлов, отображаемых в списке недавно использовавшихся, выберите в меню **Сервис** пункт **Параметры**, раскройте папку **Среда** и выберите **Общие**.  
  
    2.  Измените число в поле **Показать n файлов в списке недавно использованных**.  
  
## <a name="custom-report-code-sample"></a>Образец кода пользовательского отчета  
Отчет, созданный с помощью приведенного ниже кода, будет использовать параметры, связанные с узлом обозревателя объектов.  
  
```  
<pre><?xml version="1.0" encoding="utf-8"?>  
<Report xmlns="https://schemas.microsoft.com/sqlserver/reporting/2005/01/reportdefinition" xmlns:rd="https://schemas.microsoft.com/SQLServer/reporting/reportdesigner">  
<ReportParameters>  
<ReportParameter Name="ObjectName">  
<DataType>String</DataType>  
<Nullable>true</Nullable>  
<AllowBlank>true</AllowBlank>  
<Prompt>ObjectName</Prompt>  
</ReportParameter>  
<ReportParameter Name="ObjectTypeName">  
<DataType>String</DataType>  
<Nullable>true</Nullable>  
<AllowBlank>true</AllowBlank>  
<Prompt>ObjectTypeName</Prompt>  
</ReportParameter>  
<ReportParameter Name="Filtered">  
<DataType>Boolean</DataType>  
<Nullable>true</Nullable>  
<AllowBlank>true</AllowBlank>  
<Prompt>Filtered</Prompt>  
</ReportParameter>  
<ReportParameter Name="ServerName">  
<DataType>String</DataType>  
<Nullable>true</Nullable>  
<AllowBlank>true</AllowBlank>  
<Prompt>ServerName</Prompt>  
</ReportParameter>  
<ReportParameter Name="FontName">  
<DataType>String</DataType>  
<DefaultValue>  
<Values>  
<Value>Tahoma</Value>  
</Values>  
</DefaultValue>  
<AllowBlank>true</AllowBlank>  
<Prompt>FontName</Prompt>  
</ReportParameter>  
<ReportParameter Name="DatabaseName">  
<DataType>String</DataType>  
<Nullable>true</Nullable>  
<DefaultValue>  
<Values>  
<Value>master</Value>  
</Values>  
</DefaultValue>  
<AllowBlank>true</AllowBlank>  
<Prompt>DatabaseName</Prompt>  
</ReportParameter>  
</ReportParameters>  
<DataSources>  
<DataSource Name="AllReportParameters">  
<ConnectionProperties>  
<IntegratedSecurity>true</IntegratedSecurity>  
<ConnectString>Data Source=.</ConnectString>  
<DataProvider>SQL</DataProvider>  
</ConnectionProperties>  
<rd:DataSourceID>f1feee4c-0fdc-4301-9efa-3cd89eed2d9f</rd:DataSourceID>  
</DataSource>  
</DataSources>  
<BottomMargin>1in</BottomMargin>  
<RightMargin>1in</RightMargin>  
<rd:DrawGrid>true</rd:DrawGrid>  
<InteractiveWidth>8.5in</InteractiveWidth>  
<rd:SnapToGrid>true</rd:SnapToGrid>  
<Body>  
<ReportItems>  
<Textbox Name="textbox1">  
<rd:DefaultName>textbox1</rd:DefaultName>  
<ZIndex>1</ZIndex>  
<Width>6in</Width>  
<Style>  
<PaddingLeft>2pt</PaddingLeft>  
<PaddingBottom>2pt</PaddingBottom>  
<FontFamily>Tahoma</FontFamily>  
<FontWeight>700</FontWeight>  
<FontSize>20pt</FontSize>  
<Color>SteelBlue</Color>  
<PaddingRight>2pt</PaddingRight>  
<PaddingTop>2pt</PaddingTop>  
</Style>  
<CanGrow>true</CanGrow>  
<Height>0.36in</Height>  
<Value>AllReportParameters</Value>  
</Textbox>  
<Table Name="table1">  
<DataSetName>AllReportParameters</DataSetName>  
<Top>0.36in</Top>  
<Details>  
<TableRows>  
<TableRow>  
<TableCells>  
<TableCell>  
<ReportItems>  
<Textbox Name="ObjectName">  
<rd:DefaultName>ObjectName</rd:DefaultName>  
<ZIndex>5</ZIndex>  
<Style>  
<BorderStyle>  
<Default>Solid</Default>  
</BorderStyle>  
<PaddingLeft>2pt</PaddingLeft>  
<PaddingBottom>2pt</PaddingBottom>  
<FontFamily>Tahoma</FontFamily>  
<BorderColor>  
<Default>LightGrey</Default>  
</BorderColor>  
<PaddingRight>2pt</PaddingRight>  
<PaddingTop>2pt</PaddingTop>  
</Style>  
<CanGrow>true</CanGrow>  
<Value>=Parameters!ObjectName.Value</Value>  
</Textbox>  
</ReportItems>  
</TableCell>  
<TableCell>  
<ReportItems>  
<Textbox Name="ObjectTypeName">  
<rd:DefaultName>ObjectTypeName</rd:DefaultName>  
<ZIndex>4</ZIndex>  
<Style>  
<BorderStyle>  
<Default>Solid</Default>  
</BorderStyle>  
<PaddingLeft>2pt</PaddingLeft>  
<PaddingBottom>2pt</PaddingBottom>  
<FontFamily>Tahoma</FontFamily>  
<BorderColor>  
<Default>LightGrey</Default>  
</BorderColor>  
<PaddingRight>2pt</PaddingRight>  
<PaddingTop>2pt</PaddingTop>  
</Style>  
<CanGrow>true</CanGrow>  
<Value>=Parameters!ObjectTypeName.Value</Value>  
</Textbox>  
</ReportItems>  
</TableCell>  
<TableCell>  
<ReportItems>  
<Textbox Name="Filtered">  
<rd:DefaultName>Filtered</rd:DefaultName>  
<ZIndex>3</ZIndex>  
<Style>  
<BorderStyle>  
<Default>Solid</Default>  
</BorderStyle>  
<PaddingLeft>2pt</PaddingLeft>  
<PaddingBottom>2pt</PaddingBottom>  
<FontFamily>Tahoma</FontFamily>  
<BorderColor>  
<Default>LightGrey</Default>  
</BorderColor>  
<PaddingRight>2pt</PaddingRight>  
<PaddingTop>2pt</PaddingTop>  
</Style>  
<CanGrow>true</CanGrow>  
<Value>=Parameters!Filtered.Value</Value>  
</Textbox>  
</ReportItems>  
</TableCell>  
<TableCell>  
<ReportItems>  
<Textbox Name="ServerName">  
<rd:DefaultName>ServerName</rd:DefaultName>  
<ZIndex>2</ZIndex>  
<Style>  
<BorderStyle>  
<Default>Solid</Default>  
</BorderStyle>  
<PaddingLeft>2pt</PaddingLeft>  
<PaddingBottom>2pt</PaddingBottom>  
<FontFamily>Tahoma</FontFamily>  
<BorderColor>  
<Default>LightGrey</Default>  
</BorderColor>  
<PaddingRight>2pt</PaddingRight>  
<PaddingTop>2pt</PaddingTop>  
</Style>  
<CanGrow>true</CanGrow>  
<Value>=Parameters!ServerName.Value</Value>  
</Textbox>  
</ReportItems>  
</TableCell>  
<TableCell>  
<ReportItems>  
<Textbox Name="FontName">  
<rd:DefaultName>FontName</rd:DefaultName>  
<ZIndex>1</ZIndex>  
<Style>  
<BorderStyle>  
<Default>Solid</Default>  
</BorderStyle>  
<PaddingLeft>2pt</PaddingLeft>  
<PaddingBottom>2pt</PaddingBottom>  
<FontFamily>Tahoma</FontFamily>  
<BorderColor>  
<Default>LightGrey</Default>  
</BorderColor>  
<PaddingRight>2pt</PaddingRight>  
<PaddingTop>2pt</PaddingTop>  
</Style>  
<CanGrow>true</CanGrow>  
<Value>=Parameters!FontName.Value</Value>  
</Textbox>  
</ReportItems>  
</TableCell>  
<TableCell>  
<ReportItems>  
<Textbox Name="DatabaseName">  
<rd:DefaultName>DatabaseName</rd:DefaultName>  
<Style>  
<BorderStyle>  
<Default>Solid</Default>  
</BorderStyle>  
<PaddingLeft>2pt</PaddingLeft>  
<PaddingBottom>2pt</PaddingBottom>  
<FontFamily>Tahoma</FontFamily>  
<BorderColor>  
<Default>LightGrey</Default>  
</BorderColor>  
<PaddingRight>2pt</PaddingRight>  
<PaddingTop>2pt</PaddingTop>  
</Style>  
<CanGrow>true</CanGrow>  
<Value>=Parameters!DatabaseName.Value</Value>  
</Textbox>  
</ReportItems>  
</TableCell>  
</TableCells>  
<Height>0.21in</Height>  
</TableRow>  
</TableRows>  
</Details>  
<Header>  
<TableRows>  
<TableRow>  
<TableCells>  
<TableCell>  
<ReportItems>  
<Textbox Name="textbox2">  
<rd:DefaultName>textbox2</rd:DefaultName>  
<ZIndex>11</ZIndex>  
<Style>  
<BorderStyle>  
<Default>Solid</Default>  
</BorderStyle>  
<PaddingLeft>2pt</PaddingLeft>  
<PaddingBottom>2pt</PaddingBottom>  
<FontFamily>Tahoma</FontFamily>  
<FontWeight>700</FontWeight>  
<FontSize>11pt</FontSize>  
<BorderColor>  
<Default>LightGrey</Default>  
</BorderColor>  
<BackgroundColor>SteelBlue</BackgroundColor>  
<Color>White</Color>  
<PaddingRight>2pt</PaddingRight>  
<PaddingTop>2pt</PaddingTop>  
</Style>  
<CanGrow>true</CanGrow>  
<Value>ObjectName</Value>  
</Textbox>  
</ReportItems>  
</TableCell>  
<TableCell>  
<ReportItems>  
<Textbox Name="textbox3">  
<rd:DefaultName>textbox3</rd:DefaultName>  
<ZIndex>10</ZIndex>  
<Style>  
<BorderStyle>  
<Default>Solid</Default>  
</BorderStyle>  
<PaddingLeft>2pt</PaddingLeft>  
<PaddingBottom>2pt</PaddingBottom>  
<FontFamily>Tahoma</FontFamily>  
<FontWeight>700</FontWeight>  
<FontSize>11pt</FontSize>  
<BorderColor>  
<Default>LightGrey</Default>  
</BorderColor>  
<BackgroundColor>SteelBlue</BackgroundColor>  
<Color>White</Color>  
<PaddingRight>2pt</PaddingRight>  
<PaddingTop>2pt</PaddingTop>  
</Style>  
<CanGrow>true</CanGrow>  
<Value>ObjectTypeName</Value>  
</Textbox>  
</ReportItems>  
</TableCell>  
<TableCell>  
<ReportItems>  
<Textbox Name="textbox4">  
<rd:DefaultName>textbox4</rd:DefaultName>  
<ZIndex>9</ZIndex>  
<Style>  
<BorderStyle>  
<Default>Solid</Default>  
</BorderStyle>  
<PaddingLeft>2pt</PaddingLeft>  
<PaddingBottom>2pt</PaddingBottom>  
<FontFamily>Tahoma</FontFamily>  
<FontWeight>700</FontWeight>  
<FontSize>11pt</FontSize>  
<BorderColor>  
<Default>LightGrey</Default>  
</BorderColor>  
<BackgroundColor>SteelBlue</BackgroundColor>  
<Color>White</Color>  
<PaddingRight>2pt</PaddingRight>  
<PaddingTop>2pt</PaddingTop>  
</Style>  
<CanGrow>true</CanGrow>  
<Value>Filtered</Value>  
</Textbox>  
</ReportItems>  
</TableCell>  
<TableCell>  
<ReportItems>  
<Textbox Name="textbox5">  
<rd:DefaultName>textbox5</rd:DefaultName>  
<ZIndex>8</ZIndex>  
<Style>  
<BorderStyle>  
<Default>Solid</Default>  
</BorderStyle>  
<PaddingLeft>2pt</PaddingLeft>  
<PaddingBottom>2pt</PaddingBottom>  
<FontFamily>Tahoma</FontFamily>  
<FontWeight>700</FontWeight>  
<FontSize>11pt</FontSize>  
<BorderColor>  
<Default>LightGrey</Default>  
</BorderColor>  
<BackgroundColor>SteelBlue</BackgroundColor>  
<Color>White</Color>  
<PaddingRight>2pt</PaddingRight>  
<PaddingTop>2pt</PaddingTop>  
</Style>  
<CanGrow>true</CanGrow>  
<Value>ServerName</Value>  
</Textbox>  
</ReportItems>  
</TableCell>  
<TableCell>  
<ReportItems>  
<Textbox Name="textbox6">  
<rd:DefaultName>textbox6</rd:DefaultName>  
<ZIndex>7</ZIndex>  
<Style>  
<BorderStyle>  
<Default>Solid</Default>  
</BorderStyle>  
<PaddingLeft>2pt</PaddingLeft>  
<PaddingBottom>2pt</PaddingBottom>  
<FontFamily>Tahoma</FontFamily>  
<FontWeight>700</FontWeight>  
<FontSize>11pt</FontSize>  
<BorderColor>  
<Default>LightGrey</Default>  
</BorderColor>  
<BackgroundColor>SteelBlue</BackgroundColor>  
<Color>White</Color>  
<PaddingRight>2pt</PaddingRight>  
<PaddingTop>2pt</PaddingTop>  
</Style>  
<CanGrow>true</CanGrow>  
<Value>FontName</Value>  
</Textbox>  
</ReportItems>  
</TableCell>  
<TableCell>  
<ReportItems>  
<Textbox Name="textbox7">  
<rd:DefaultName>textbox7</rd:DefaultName>  
<ZIndex>6</ZIndex>  
<Style>  
<BorderStyle>  
<Default>Solid</Default>  
</BorderStyle>  
<PaddingLeft>2pt</PaddingLeft>  
<PaddingBottom>2pt</PaddingBottom>  
<FontFamily>Tahoma</FontFamily>  
<FontWeight>700</FontWeight>  
<FontSize>11pt</FontSize>  
<BorderColor>  
<Default>LightGrey</Default>  
</BorderColor>  
<BackgroundColor>SteelBlue</BackgroundColor>  
<Color>White</Color>  
<PaddingRight>2pt</PaddingRight>  
<PaddingTop>2pt</PaddingTop>  
</Style>  
<CanGrow>true</CanGrow>  
<Value>DatabaseName</Value>  
</Textbox>  
</ReportItems>  
</TableCell>  
</TableCells>  
<Height>0.22in</Height>  
</TableRow>  
</TableRows>  
<RepeatOnNewPage>true</RepeatOnNewPage>  
</Header>  
<TableColumns>  
<TableColumn>  
<Width>3in</Width>  
</TableColumn>  
<TableColumn>  
<Width>1.5in</Width>  
</TableColumn>  
<TableColumn>  
<Width>0.75in</Width>  
</TableColumn>  
<TableColumn>  
<Width>1.125in</Width>  
</TableColumn>  
<TableColumn>  
<Width>2in</Width>  
</TableColumn>  
<TableColumn>  
<Width>1.375in</Width>  
</TableColumn>  
</TableColumns>  
</Table>  
</ReportItems>  
<Height>0.79in</Height>  
</Body>  
<rd:ReportID>abb14e58-fd36-495a-89ff-b66f29ef287b</rd:ReportID>  
<LeftMargin>1in</LeftMargin>  
<DataSets>  
<DataSet Name="AllReportParameters">  
<Query>  
<rd:UseGenericDesigner>true</rd:UseGenericDesigner>  
<CommandText>SELECT 1  
</CommandText>  
<DataSourceName>AllReportParameters</DataSourceName>  
</Query>  
<Fields>  
<Field Name="ObjectName">  
<rd:TypeName>System.String</rd:TypeName>  
<DataField>ObjectName</DataField>  
</Field>  
<Field Name="ObjectTypeName">  
<rd:TypeName>System.String</rd:TypeName>  
<DataField>ObjectTypeName</DataField>  
</Field>  
<Field Name="Filtered">  
<rd:TypeName>System.Boolean</rd:TypeName>  
<DataField>Filtered</DataField>  
</Field>  
<Field Name="ServerName">  
<rd:TypeName>System.String</rd:TypeName>  
<DataField>ServerName</DataField>  
</Field>  
<Field Name="FontName">  
<rd:TypeName>System.String</rd:TypeName>  
<DataField>FontName</DataField>  
</Field>  
<Field Name="DatabaseName">  
<rd:TypeName>System.String</rd:TypeName>  
<DataField>DatabaseName</DataField>  
</Field>  
</Fields>  
</DataSet>  
</DataSets>  
<Width>6.875in</Width>  
<InteractiveHeight>11in</InteractiveHeight>  
<Language>en-US</Language>  
<TopMargin>1in</TopMargin>  
</Report></pre>  
```

## <a name="see-also"></a>См. также:  
[Пользовательские отчеты в среде Management Studio](../../ssms/object/custom-reports-in-management-studio.md)  
[Добавление пользовательского отчета в среду Management Studio](../../ssms/object/add-a-custom-report-to-management-studio.md)  
[Отмена скрытия предупреждений для пользовательских отчетов](../../ssms/object/unsuppress-run-custom-report-warnings.md)  
  

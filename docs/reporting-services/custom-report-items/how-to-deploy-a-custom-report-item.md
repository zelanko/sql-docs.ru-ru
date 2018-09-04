---
title: Развертывание пользовательского элемента отчета | Документы Майкрософт
ms.date: 03/18/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: custom-report-items
ms.suite: pro-bi
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom report items, deploying
ms.assetid: 80e97b0d-e355-4240-aebd-08cbc84089ed
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 3a60168c436700dfbe01a81fbd33f292fdfef49d
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2018
ms.locfileid: "43276126"
---
# <a name="how-to-deploy-a-custom-report-item"></a>Развертывание пользовательского элемента отчета
  Чтобы развернуть пользовательский элемент отчета в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], нужно изменить файлы конфигурации сервера отчетов и скопировать сборки времени разработки и времени выполнения в соответствующие папки приложений для конструктора отчетов и сервера отчетов.  
  
### <a name="to-deploy-a-custom-report-item"></a>Развертывание пользовательского элемента отчета  
  
1.  Произведите редактирование файла Rsreportdesigner.config, настроив компоненты времени разработки и компоненты времени выполнения, принадлежащие пользовательскому элементу отчета, для использования в конструкторе.  Обратите внимание на то, что запись **ReportItemName** должна соответствовать атрибуту **CustomReportItemAttribute**, используемому в классе **CustomReportItemDesigner**. Пример:  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    <ReportItemDesigner>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsDesigner, PolygonsDesigner" />  
    </ReportItemDesigner>  
    <ReportItemConverter>  
       <Converter Source="Chart" Target="Polygons" Type="PolygonsCRI.PolygonsConverter, PolygonsDesigner" />  
    </ReportItemConverter>  
    ```  
  
2.  Произведите редактирование файла Rsreportdesigner.config, зарегистрировав компонент времени выполнения пользовательского элемента отчета. Пример:  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    ```  
  
3.  Отредактируйте файл Rsssrvpolicy.config, добавив запись **CodeGroup**, предоставляющую соответствующие разрешения для пользовательского элемента отчета. Пример:  
  
    ```  
    <CodeGroup   
       class="UnionCodeGroup"   
       version="1"   
       PermissionSetName="FullTrust"  
       Description="This code group grants MyCustomReportItem.dll FullTrust permission. ">  
       <IMembershipCondition   
          class="UrlMembershipCondition"  
          version="1"  
       Url="C:\Program Files\Microsoft SQL Server\ MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin\MyCustomReportItem.dll" />  
    </CodeGroup>  
    ```  
  
4.  Скопируйте динамическую библиотеку компонента времени выполнения пользовательского элемента отчета в каталоги %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies и \Program Files\Microsoft SQL Server\MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin.  
  
5.  Скопируйте динамическую библиотеку компонента времени разработки пользовательского элемента отчета в каталог %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.  
  
## <a name="see-also"></a>См. также:  
 [Файлы конфигурации служб Reporting Services](../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Библиотеки классов пользовательских элементов отчета](../../reporting-services/custom-report-items/custom-report-item-class-libraries.md)  
  
  

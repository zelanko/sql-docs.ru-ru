---
title: Занятие 2. Создание классов из RDL-схемы с помощью средства XSD | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a81c87f1-7977-4b30-b6ac-b38b3e2b6398
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: f5f74c6621d329885e9149fce9a37c7418d9c37b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62653757"
---
# <a name="lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool"></a>Урок 2. Формирование классов из RDL-схемы с помощью инструмента xsd
  После создания проекта в среде [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] следующим шагом является получение локальной копии схемы определения отчета и запуск средства определения XML-схемы (Xsd.exe).  
  
### <a name="to-generate-the-rdl-classes"></a>Формирование RDL-классов  
  
1.  Откройте экземпляр [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer (или аналогичный веб-браузер) и перейдите по следующему URL-адресу:  
  
    ```  
    https://schemas.microsoft.com/sqlserver/reporting/2010/01/reportdefinition/ReportDefinition.xsd  
    ```  
  
2.  После открытия схемы языка определения отчетов в браузере перейдите в меню **файл** и выберите **Сохранить как**.  
  
3.  Перейдите в папку, в которой был создан проект [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], и сохраните файл схемы под именем ReportDefinition.xsd.  
  
4.  После сохранения файла откройте экземпляр [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] командной строки. Чтобы открыть экземпляр командной строки, в меню Пуск последовательно выберите пункты **все программы**, **Microsoft Visual Studio 2010**, **инструменты Visual Studio** и щелкните **Командная строка Visual Studio (2010)**.  
  
5.  Перейдите в папку, в которой сохранен файл ReportDefinition.xsd:  
  
     `CD\<ReportDefinition.xsd Path>`  
  
6.  Создайте файл ReportDefinition.cs, содержащий классы для RDL-схемы, выполнив следующую команду:  
  
     `xsd /c /n:SampleRDLSchema ReportDefinition.xsd`  
  
     Для создания файла ReportDefinition.vb используйте команду:  
  
     `xsd /c /l:VB /n:SampleRDLSchema ReportDefinition.xsd`  
  
7.  Добавьте файл ReportDefinition.xsd в проект. В меню **проект** выберите команду **Добавить существующий элемент**. Перейдите к расположению файла ReportDefinition. xsd, выберите ReportDefinition. xsd и нажмите кнопку **Добавить**.  
  
    > [!NOTE]  
    >  После добавления файла ReportDefinition. xsd в проект вы увидите в **Обозреватель решений** что файл ReportDefinition.cs (VB) отсутствует. Чтобы отобразить файл, нажмите кнопку разворачивания или сворачивания рядом с файлом ReportDefinition.xsd.  
  
## <a name="next-lesson"></a>Следующее занятие  
 На следующем занятии будет написан код для загрузки определения отчета с сервера отчетов с помощью классов, сформированных из RDL-схемы.  См. [занятие 3. Загрузка определения отчета с сервера отчетов](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md).  
  
## <a name="see-also"></a>См. также:  
 [Обновление отчетов с использованием классов, созданных из учебника по схеме языка определения отчетов &#40;SSRS&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [Язык определения отчетов &#40;службы SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  

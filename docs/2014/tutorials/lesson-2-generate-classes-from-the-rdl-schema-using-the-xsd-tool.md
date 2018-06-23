---
title: 'Занятие 2: Создать классы из RDL-схемы с помощью инструмента xsd | Документы Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a81c87f1-7977-4b30-b6ac-b38b3e2b6398
caps.latest.revision: 13
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 67cbc84882683fcb31d6b42f69274d5166556450
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194620"
---
# <a name="lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool"></a>Занятие 2: Создать классы из RDL-схемы с помощью инструмента xsd
  После создания проекта в среде [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] следующим шагом является получение локальной копии схемы определения отчета и запуск средства определения XML-схемы (Xsd.exe).  
  
### <a name="to-generate-the-rdl-classes"></a>Формирование RDL-классов  
  
1.  Откройте экземпляр [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer (или эквивалентный веб-браузер) и перейдите к следующему URL-АДРЕСУ:  
  
    ```  
    http://schemas.microsoft.com/sqlserver/reporting/2010/01/reportdefinition/ReportDefinition.xsd  
    ```  
  
2.  После открытия схемы языка определения Отчетов в браузере перейдите к **файл** и выбрать пункт **Сохранить как**.  
  
3.  Перейдите в папку, в которой был создан проект [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], и сохраните файл схемы под именем ReportDefinition.xsd.  
  
4.  После сохранения файла откройте экземпляр [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] командной строки. Чтобы открыть экземпляр командной строки, нажмите кнопку Пуск, выберите команду **все программы**, пункты **Microsoft Visual Studio 2010**, пункты **набора средств Visual Studio** и нажмите кнопку **Командную строку visual Studio (2010)**.  
  
5.  Перейдите в папку, в которой сохранен файл ReportDefinition.xsd:  
  
     `CD\<ReportDefinition.xsd Path>`  
  
6.  Создайте файл ReportDefinition.cs, содержащий классы для RDL-схемы, выполнив следующую команду:  
  
     `xsd /c /n:SampleRDLSchema ReportDefinition.xsd`  
  
     Для создания файла ReportDefinition.vb используйте команду:  
  
     `xsd /c /l:VB /n:SampleRDLSchema ReportDefinition.xsd`  
  
7.  Добавьте файл ReportDefinition.xsd в проект. Из **проекта** меню, нажмите кнопку **Добавление существующего элемента**. Перейдите к расположению файла ReportDefinition.xsd, выделите его и нажмите кнопку **добавить**.  
  
    > [!NOTE]  
    >  После добавления в проект файла ReportDefinition.xsd можно заметить в **обозревателе решений** что файла ReportDefinition.cs (VB) не существует. Чтобы отобразить файл, нажмите кнопку разворачивания или сворачивания рядом с файлом ReportDefinition.xsd.  
  
## <a name="next-lesson"></a>Следующее занятие  
 На следующем занятии будет написан код для загрузки определения отчета с сервера отчетов с помощью классов, сформированных из RDL-схемы.  В разделе [Lesson 3: Загрузка определения отчета с сервера отчетов](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md).  
  
## <a name="see-also"></a>См. также  
 [Обновление отчетов с помощью классов, созданных из RDL-схемы &#40;учебник по службам SSRS&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [Язык определения отчетов (службы SSRS)](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
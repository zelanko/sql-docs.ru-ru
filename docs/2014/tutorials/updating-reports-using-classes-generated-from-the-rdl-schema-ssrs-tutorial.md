---
title: Обновление отчетов с помощью классов, созданных из RDL-схемы (учебник по службам SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- RDL [Reporting Services], generating
- RDL [Reporting Services], tutorials
- RDL [Reporting Services], serializing
ms.assetid: 8f81d48f-7ab9-4ef8-bce0-7d16d9a47fbd
caps.latest.revision: 26
author: craigg-msft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 96d125a3d69b564c94b64d23f825778c55068991
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297564"
---
# <a name="updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial"></a>Обновление отчетов с помощью классов, созданных из схемы языка определения отчетов (учебник по службам SSRS)
  Этот учебник демонстрирует, как использовать инструмент определения схемы XML (Xsd.exe) создавать классы, позволяющие сериализацию и десериализацию файлов определения отчета (RDL и RDLC) с [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.Xml.Serialization.XmlSerializer> класса.  
  
## <a name="what-you-will-learn"></a>Обзор учебника  
 В ходе работы с этим учебником предстоит выполнить следующие действия.  
  
-   Создание приложения с помощью [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] шаблон проекта консольного приложения.  
  
-   Создать классы из схемы языка определения отчетов (RDL) с помощью **xsd** средство.  
  
-   Подключиться к серверу отчетов и получить определение отчета.  
  
-   Написать код для обновления файла определения отчета.  
  
-   Сохранить обновленное определение отчета на сервере отчетов.  
  
-   Выполнение приложения схемы языка определения отчетов (VB/C#).  
  
> [!NOTE]  
>  Образцы кода, приведенные в этом учебнике, могут не работать в отчетах, у которых нет описания. Происходит это потому, что у отчетов, для которых не задано описание, отсутствует свойство описания.  
  
## <a name="requirements"></a>Требования  
 Для работы с учебником необходимо наличие следующих компонентов.  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].  
  
-   Необходимые разрешения для доступа к отчетам и публикации их в веб-службе сервера отчетов SQL Server на компьютере, на котором размещен сервер отчетов.  
  
-   Образец базы данных [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)], установленный на экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Отчет, установленный на сервере отчетов. Этот учебник основывается на образце отчета Company Sales 2012. Дополнительные сведения об образцах отчетов см. в разделе [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
> [!NOTE]  
>  Образцы не устанавливаются автоматически в процессе установки, но их можно установить в любое время. Сведения об образцах см. в разделе [SQL Server Product Samples](http://go.microsoft.com/fwlink/?LinkId=182887).  
  
 **Предполагаемое время для работы с учебником:** 30 минут  
  
## <a name="tasks"></a>Задания  
 [Урок 1. Создание проекта Visual Studio "RDL-схема"](../../2014/tutorials/lesson-1-create-the-rdl-schema-visual-studio-project.md)  
  
 [Урок 2. Формирование классов из RDL-схемы с помощью инструмента xsd](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md)  
  
 [Урок 3. Загрузка определения отчета с сервера отчетов](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md)  
  
 [Урок 4. Обновление определения отчета программным способом](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md)  
  
 [Урок 5. Публикация определения отчета на сервере отчетов](../../2014/tutorials/lesson-5-publish-the-report-definition-to-the-report-server.md)  
  
 [Урок 6: Выполнение приложения RDL-схемы &#40;VB-C&#35;&#41;](../../2014/tutorials/lesson-6-run-the-rdl-schema-application-vb-csharp.md)  
  
## <a name="see-also"></a>См. также  
 [Язык определения отчетов (службы SSRS)](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  

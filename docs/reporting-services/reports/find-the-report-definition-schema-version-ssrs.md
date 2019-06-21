---
title: Определение версии схемы определения отчета (службы SSRS) | Документы Майкрософт
ms.date: 06/06/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reports
ms.topic: conceptual
helpviewer_keywords:
- XML schemas [Reporting Services]
- Report Definition Language, XML schema
- schemas [Reporting Services]
ms.assetid: 67954419-1b61-4481-a3b9-23b4ba7a5624
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 129fcb8e1533162560b88e9400c68c7c863be119
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66826839"
---
# <a name="find-the-report-definition-schema-version-ssrs"></a>Определение версии схемы определения отчета (SSRS)

В файле определения отчета указывается пространство имен языка определения отчетов для версии схемы определения отчета, использованной для проверки RDL-файла. При открытии RDL-файл в среде, такой как конструктор отчетов в среде разработки отчетов [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], Visual Studio или построителе отчетов. Если отчет был создан в предыдущем пространстве имен, автоматически создается файл резервной копии и отчет обновляется до текущего пространства имен. Если сохранить обновленное определение отчета, будет сохранен преобразованный RDL-файл. Это единственный способ обновления определения отчетов. Само определение отчетов не обновляется на сервере отчетов. Скомпилированный отчет обновляется на сервере отчетов. Дополнительные сведения см. в разделе [Upgrade Reports](../../reporting-services/install-windows/upgrade-reports.md).  
  
## <a name="how-to-identify-the-rdl-schema-version-of-a-report"></a>Практическое руководство. Определение версии RDL-схемы отчета  
  
1. Откройте файл .rdl отчета в приложении (например, в Блокноте или XML Notepad 2007), в котором можно просматривать код XML.  
  
     XML-элемент Report указывает пространство имен схемы. Например, следующий элемент Report указывает пространство имен для конструктора отчетов и пространство имен для определения отчета.  
  
    ``` XML 
    <Report xmlns:rd="http://schemas.microsoft.com/SQLServer/reporting/reportdesigner" xmlns="http://schemas.microsoft.com/sqlserver/reporting/2016/01/reportdefinition" xmlns:df="http://schemas.microsoft.com/sqlserver/reporting/2016/01/reportdefinition/defaultfontfamily" MustUnderstand="df">  
    ```  
  
     Последнее пространство имен определения отчетов — 2016. Тем не менее, последнее пространство имен определения опубликованного отчета — 2010, определяемое следующий URL-адрес: `https://schemas.microsoft.com/sqlserver/reporting/2010/01/reportdefinition`...
  
### <a name="how-to-identify-the-rdl-schema-version-of-report-designer"></a>Практическое руководство. Определение версии RDL-схемы конструктора отчетов  
  
1.  Открыть новый проект. Версия выбранного проекта определяет версию схемы языка определения отчетов. В SQL Server поддерживается использование нескольких версий схемы. Дополнительные сведения см. в разделе [Развертывание и поддержка версий в SQL Server Data Tools](../../reporting-services/tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md).  
  
2.  В меню **Проект** выберите **Добавить новый элемент**. Откроется диалоговое окно **Добавление нового элемента** .  
  
3.  На панели **Шаблоны** нажмите кнопку **Отчет**.  
  
4.  В поле **Имя**введите имя отчета или примите имя по умолчанию.  
  
5.  Нажмите кнопку **Добавить**. Конструктор отчетов открывает новый пустой отчет в режиме конструктора.  
  
6.  В меню **Вид** выберите пункт **Код**. Определение отчета отображается в виде XML-файла.  
  
    XML-элемент Report указывает пространство имен схемы. Например, следующий элемент Report указывает пространство имен для конструктора отчетов и пространство имен для определения отчета.  
  
    ``` XML 
    <Report xmlns:rd="http://schemas.microsoft.com/SQLServer/reporting/reportdesigner" xmlns="http://schemas.microsoft.com/sqlserver/reporting/*year*/01/reportdefinition" xmlns:df="http://schemas.microsoft.com/sqlserver/reporting/*year*/01/reportdefinition/defaultfontfamily" MustUnderstand="df">  
    ```  
  
     Пространство имен определения отчета указано следующим URL-адресом: `https://schemas.microsoft.com/sqlserver/reporting/*year*/01/reportdefinition`  
  
### <a name="how-to-identify-the-rdl-schema-version-on-the-report-server"></a>Практическое руководство. Определение версии RDL-схемы отчета на сервере отчетов  
  
-   В веб-портала введите URL-адрес для сервера отчетов. Например, следующий URL-адрес указывает сервер отчетов на локальном компьютере.  
  
     `https://localhost/reportserver/reportdefinition.xsd`  
  
     XSD-файл открывается в браузере.  
  
     Элемент XML-схемы указывает пространство имен схемы. Например, следующий элемент схемы указывает три пространства имен: ссылку targetNamespace, которая используется в среде [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], XSD-ссылку для самой схемы (XSD) и ссылку определения отчета.  *Год* представляет год в отчете используется схемы. Например, 2010 или 2016.
  
    ``` XML  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/sqlserver/reporting/*year*/01/reportdefinition" targetNamespace="http://schemas.microsoft.com/sqlserver/reporting/*year*/01/reportdefinition" elementFormDefault="qualified">  
    ```  
  
     Пространство имен определения отчета указано следующим URL-адресом: `https://schemas.microsoft.com/sqlserver/reporting/*year*/01/reportdefinition`  

## <a name="next-steps"></a>Следующие шаги
[Обновление отчетов](../../reporting-services/install-windows/upgrade-reports.md)   
[Язык определения отчетов](../../reporting-services/reports/report-definition-language-ssrs.md)   

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).

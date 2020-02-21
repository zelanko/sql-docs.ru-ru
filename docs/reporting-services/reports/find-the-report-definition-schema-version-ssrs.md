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
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "66826839"
---
# <a name="find-the-report-definition-schema-version-ssrs"></a>Определение версии схемы определения отчета (SSRS)

В файле определения отчета указывается пространство имен языка определения отчетов для версии схемы определения отчета, использованной для проверки RDL-файла. Например, можно открыть отчет, который был создан в другой среде создания отчетов, такой как конструктор отчетов в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], Visual Studio или построитель отчетов. Если отчет был создан в прежнем пространстве имен, автоматически создается файл резервной копии и отчет обновляется до текущего пространства имен. Если сохранить обновленное определение отчета, будет сохранен преобразованный RDL-файл. Это единственный способ обновления определения отчетов. Само определение отчетов не обновляется на сервере отчетов. Скомпилированный отчет обновляется на сервере отчетов. Дополнительные сведения см. в разделе [Upgrade Reports](../../reporting-services/install-windows/upgrade-reports.md).  
  
## <a name="how-to-identify-the-rdl-schema-version-of-a-report"></a>Руководство. Определение версии RDL-схемы для отчета  
  
1. Откройте файл .rdl отчета в приложении (например, в Блокноте или XML Notepad 2007), в котором можно просматривать код XML.  
  
     XML-элемент Report указывает пространство имен схемы. Например, следующий элемент Report указывает пространство имен для конструктора отчетов и пространство имен для определения отчета.  
  
    ``` XML 
    <Report xmlns:rd="http://schemas.microsoft.com/SQLServer/reporting/reportdesigner" xmlns="http://schemas.microsoft.com/sqlserver/reporting/2016/01/reportdefinition" xmlns:df="http://schemas.microsoft.com/sqlserver/reporting/2016/01/reportdefinition/defaultfontfamily" MustUnderstand="df">  
    ```  
  
     Для определения отчета самым последним считается пространство имен 2016. Но среди опубликованных для определения отчета самым последним является пространство имен 2010, определенное следующим URL-адресом: `https://schemas.microsoft.com/sqlserver/reporting/2010/01/reportdefinition`.
  
### <a name="how-to-identify-the-rdl-schema-version-of-report-designer"></a>Руководство. Определение версии RDL-схемы конструктора отчетов  
  
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
  
### <a name="how-to-identify-the-rdl-schema-version-on-the-report-server"></a>Руководство. Определение версии RDL-схемы на сервере отчетов  
  
-   На веб-портале введите URL-адрес сервера отчетов. Например, следующий URL-адрес указывает сервер отчетов на локальном компьютере.  
  
     `https://localhost/reportserver/reportdefinition.xsd`  
  
     XSD-файл открывается в браузере.  
  
     Элемент XML-схемы указывает пространство имен схемы. Например, следующий элемент схемы указывает три пространства имен: ссылку targetNamespace, которая используется в среде [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], XSD-ссылку для самой схемы (XSD) и ссылку определения отчета.  *Year* обозначает год издания схемы, которая используется отчетом. Например, 2010 или 2016.
  
    ``` XML  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/sqlserver/reporting/*year*/01/reportdefinition" targetNamespace="http://schemas.microsoft.com/sqlserver/reporting/*year*/01/reportdefinition" elementFormDefault="qualified">  
    ```  
  
     Пространство имен определения отчета указано следующим URL-адресом: `https://schemas.microsoft.com/sqlserver/reporting/*year*/01/reportdefinition`  

## <a name="next-steps"></a>Дальнейшие действия
[Обновление отчетов](../../reporting-services/install-windows/upgrade-reports.md)   
[Язык определения отчетов](../../reporting-services/reports/report-definition-language-ssrs.md)   

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).

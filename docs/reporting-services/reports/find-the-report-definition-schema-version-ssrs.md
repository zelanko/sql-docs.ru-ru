---
title: Определение версии схемы определения отчета (службы SSRS) | Документы Майкрософт
ms.date: 05/30/2017
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
ms.openlocfilehash: 67f1311e3f8bde71c52301178bf242d88e62c3a0
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65576419"
---
# <a name="find-the-report-definition-schema-version-ssrs"></a>Определение версии схемы определения отчета (SSRS)

В файле определения отчета указывается пространство имен языка определения отчетов для версии схемы определения отчета, использованной для проверки RDL-файла. Если RDL-файл открывается в среде разработки отчетов, такой как конструктор в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , или построителе отчетов и если отчет был создан в предыдущем пространстве имен, автоматически создается файл резервной копии и отчет обновляется до текущего пространства имен. Если сохранить обновленное определение отчета, будет сохранен преобразованный RDL-файл. Это единственный способ обновления определения отчетов. Само определение отчетов не обновляется на сервере отчетов. Скомпилированный отчет обновляется на сервере отчетов. Дополнительные сведения см. в разделе [Upgrade Reports](../../reporting-services/install-windows/upgrade-reports.md).  
  
### <a name="how-to-identify-the-rdl-schema-version-of-a-report"></a>Инструкции. Определение версии RDL-схемы отчета  
  
1.  Откройте файл отчета в формате RDL в приложении, таком как «Блокнот» или XML Notepad 2007, пригодном для просмотра XML-кода.  
  
     XML-элемент Report указывает пространство имен схемы. Например, следующий элемент Report указывает пространство имен для конструктора отчетов и пространство имен для определения отчета.  
  
    ```  
    <Report xmlns:rd=https://schemas.microsoft.com/SQLServer/reporting/reportdesigner   
    xmlns="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition">  
    ```  
  
     Пространство имен определения отчета указано следующим URL-адресом: `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`.  
  
### <a name="how-to-identify-the-rdl-schema-version-of-report-designer"></a>Как определить версию RDL-схемы конструктора отчетов  
  
1.  Открыть новый проект. Версия выбранного проекта определяет версию схемы языка определения отчетов. В SQL Server поддерживается использование нескольких версий схемы. Дополнительные сведения см. в разделе [Развертывание и поддержка версий в SQL Server Data Tools](../../reporting-services/tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md).  
  
2.  В меню **Проект** выберите **Добавить новый элемент**. Откроется диалоговое окно **Добавление нового элемента** .  
  
3.  На панели **Шаблоны** нажмите кнопку **Отчет**.  
  
4.  В поле **Имя**введите имя отчета или примите имя по умолчанию.  
  
5.  Нажмите кнопку **Добавить**. Конструктор отчетов открывает новый пустой отчет в режиме конструктора.  
  
6.  В меню **Вид** выберите пункт **Код**. Определение отчета отображается в виде XML-файла.  
  
     XML-элемент Report указывает пространство имен схемы. Например, следующий элемент Report указывает пространство имен для конструктора отчетов и пространство имен для определения отчета.  
  
    ```  
    <Report xmlns:rd=https://schemas.microsoft.com/SQLServer/reporting/reportdesigner  
    xmlns="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition">  
    ```  
  
     Пространство имен определения отчета указано следующим URL-адресом: `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`  
  
### <a name="how-to-identify-the-rdl-schema-version-on-the-report-server"></a>Инструкции. Определение версии RDL-схемы отчета на сервере отчетов  
  
-   В диспетчере отчетов введите URL-адрес сервера отчетов. Например, следующий URL-адрес указывает сервер отчетов на локальном компьютере.  
  
     `https://localhost/reportserver/reportdefinition.xsd`  
  
     XSD-файл открывается в браузере.  
  
     Элемент XML-схемы указывает пространство имен схемы. Например, следующий элемент схемы указывает три пространства имен: ссылку targetNamespace, которая используется в среде [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], XSD-ссылку для самой схемы (XSD) и ссылку определения отчета.  
  
    ```  
    <xsd:schema   
    targetNamespace="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition"   
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
    xmlns="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition"   
    elementFormDefault="qualified">  
    ```  
  
     Пространство имен определения отчета указано следующим URL-адресом: `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`  

## <a name="next-steps"></a>Следующие шаги

[Обновление отчетов](../../reporting-services/install-windows/upgrade-reports.md)   
[Язык определения отчетов](../../reporting-services/reports/report-definition-language-ssrs.md)  

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).

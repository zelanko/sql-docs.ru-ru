---
title: Мастер экспорта и импорта SQL Server | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- exporting data
- mapping files [Integration Services]
- SQL Server Import and Export Wizard
- SSIS packages, creating
- packages [Integration Services], copying
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
- Import and Export Wizard
- copying data [Integration Services]
- importing data, SSIS packages
- sources [Integration Services], copying data
ms.assetid: c0e4d867-b2a9-4b2a-844b-2fe45be88f81
caps.latest.revision: 87
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 3e320ff0fdb834ca242739a76fb9e0b1242e3579
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191249"
---
# <a name="sql-server-import-and-export-wizard"></a>мастер импорта и экспорта SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Мастер импорта и экспорта предлагает простой способ создания [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] пакет, который копирует данные из источника в место назначения.  
  
> [!NOTE]  
>  На 64-разрядном компьютере службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] устанавливают 64-разрядную версию мастера импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (DTSWizard.exe). Однако некоторые источники данных, такие как Access и Excel, располагают только 32-разрядным поставщиком. Для работы с этими источниками данных необходимо установить и запустить 32-разрядную версию мастера. Чтобы установить 32-разрядной версии мастера, необходимо выбрать клиентские средства или [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] во время установки.  
  
 Можно запустить мастер импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из меню «Пуск», из среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или из среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] либо из командной строки. Дополнительные сведения см. в разделе [запустить мастер экспорта и импорта SQL Server](start-the-sql-server-import-and-export-wizard.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Мастер импорта и экспорта можно копировать данные из любого источника данных для которого управляемый [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] доступен поставщик данных или собственного поставщика OLE DB. Доступны поставщики для следующих источников данных.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Неструктурированные файлы  
  
-   Microsoft Office Access  
  
-   Microsoft Office Excel  
  
 Некоторые функции мастера работают по-разному в зависимости от среды, в которой он вызывается.  
  
-   При запуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] мастер импорта и экспорта в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], немедленно запустить пакет, выбрав **выполнить немедленно** флажок. По умолчанию этот флажок установлен, и пакет запускается немедленно.  
  
     Можно также сохранить пакет в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или в файловой системе. При сохранении пакета необходимо также указать уровень защиты пакета. Дополнительные сведения об уровнях защиты пакета см. в разделе [Access Control for Sensitive Data in Packages](../security/access-control-for-sensitive-data-in-packages.md).  
  
     После [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] мастер импорта и экспорта создал пакет и скопировал данные, можно использовать [!INCLUDE[ssIS](../../includes/ssis-md.md)] конструктора, чтобы открыть и изменить сохраненный пакет, добавив задач, преобразований и событийно управляемой логики.  
  
    > [!NOTE]  
    >  В [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], параметр, чтобы сохранить пакет, созданный мастером недоступен.  
  
-   При запуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] мастер импорта и экспорта из [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] проекта в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], пакет не может выполняться в ходе завершения работы мастера. Вместо этого пакет добавляется в проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], из которого был запущен мастер. В дальнейшем при помощи конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] можно выполнить пакет или расширить его, включив дополнительные задачи, преобразования и логику обработки событий.  
  
 Дополнительные сведения см. в разделе [запустить мастер экспорта и импорта SQL Server](start-the-sql-server-import-and-export-wizard.md).  
  
## <a name="permissions-required-by-the-import-and-export-wizard"></a>Разрешения, необходимые для работы мастера импорта и экспорта  
 Для завершения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] мастер импорта и экспорта успешно, необходимо по крайней мере иметь следующие разрешения:  
  
-   Разрешение на подключение к исходным и целевым базам данных, а также к общим папкам. В [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], это требует прав входа в систему сервера и базы данных.  
  
-   Разрешение на считывание данных из базы данных-источника или файла-источника. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], это требует разрешения SELECT для исходных таблиц и представлений.  
  
-   Разрешение на запись данных в целевую базу данных или файл. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], для этого требуются разрешения INSERT для целевых таблиц.  
  
-   Разрешения, достаточные для создания целевой базы данных, таблицы или файла, если нужно создать новую целевую базу данных, таблицу или файл. В службах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для этого требуются разрешения CREATE DATABASE или CREATE TABLE.  
  
-   Если вы хотите сохранить пакет, созданный мастером, разрешения, достаточные для записи в базе данных msdb или в файловой системе. В [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], для этого требуются разрешения INSERT в базе данных msdb.  
  
## <a name="mapping-data-types-in-the-import-and-export-wizard"></a>Сопоставление типов данных в мастере импорта и экспорта  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Мастера импорта и экспорта предоставляет минимальные возможности преобразования. Мастер импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает преобразований на уровне столбцов за исключением выбора имени, типа данных и свойств типа данных для столбцов в новых целевых таблицах и файлах.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Мастер импорта и экспорта использует сопоставление файлов, в которой [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] предоставляет для сопоставления типов данных из одной версии базы данных или системы в другую. Например, он может сопоставить типы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и Oracle. Файлы сопоставления в формате XML по умолчанию устанавливаются в каталог «C:\Program Files\Microsoft SQL Server\100\DTS\MappingFiles». Если требуются различные сопоставления между типами данных, то можно обновить сопоставления, чтобы изменить сопоставления, выполняемые мастером. Например, если вы хотите [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **nchar** тип данных для сопоставления с DB2 **ГРАФИЧЕСКИЕ** тип данных вместо DB2 **VARGRAPHIC** при передаче данных из типа данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DB2, изменить **nchar** сопоставление в файле сопоставления SqlClientToIBMDB2.xml **ГРАФИЧЕСКИЕ** вместо **VARGRAPHIC.**  
  
 Службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] включают сопоставления между многими часто используемыми сочетаниями источников и назначений. Также можно добавить новые файлы сопоставления в каталог файлов сопоставления для поддержки дополнительных источников и назначений. Новые файлы сопоставления должны быть согласованы с опубликованной XSD-схемой и должны выполнять сопоставления между уникальными сочетаниями, источниками и назначениями.  
  
> [!NOTE]  
>  При редактировании существующего файла сопоставления, или Добавление нового файла сопоставления в папку, необходимо закрыть и снова открыть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] мастер импорта и экспорта или [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] для новые или измененные файлы были распознаны.  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
-   Видео, [Экспорт данных SQL Server в Excel (видеоматериал по SQL Server)](http://go.microsoft.com/fwlink/?LinkID=200975), на сайте technet.microsoft.com  
  
-   Образец CodePlex [Экспорт из ODBC в неструктурированный файл с помощью учебник по мастеру: пакеты занятий](http://go.microsoft.com/fwlink/?LinkId=217657), на сайте msftisprodsamples.codeplex.com  
  
  
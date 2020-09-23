---
title: Разработка баз, ориентированная на проекты, с помощью программ командной строки
description: Просмотрите доступные ресурсы в программах командной строки, которые SQL Server Data Tools предоставляет для работы с DACPAC-файлами, например SQLPackage.exe и dbSqlPackage.
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
ms.assetid: 9a26def9-8fbd-43e4-9e57-414840b73ed8
author: markingmyname
ms.author: maghan
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 04/26/2017
ms.openlocfilehash: f596b6a6d7e5d996d89b0d351396115bf9922638
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2020
ms.locfileid: "87934101"
---
# <a name="project-oriented-database-development-using-command-line-tools"></a>Разработка баз, ориентированная на проекты, с помощью программ командной строки

В состав SQL Server Data Tools входят программы командной строки, при помощи которых можно реализовать ряд сценариев разработки баз данных с учетом проекта.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-|-|  
|[SqlPackage.exe](../tools/sqlpackage.md)|В этом разделе описывается программа SQLPackage.exe, позволяющая решать следующие задачи:<br /><br />– извлечение DACPAC-файла из активной базы данных SQL Server;<br />– публикация DACPAC-файла в активной базе данных SQL Server для добавочного обновления схемы активной базы данных для соответствия с DACPAC-файлом;<br />– сравнение DACPAC-файла с активной базой данных SQL Server и создание скрипта Transact\-SQL для добавочного обновления без обновления активной базы данных;<br />– сравнение двух DACPAC-файлов для создания скрипта Transact\-SQL для добавочного обновления;<br />– создание XML-отчета со сводкой изменений, которые будут внесены в случае добавочного обновления базы данных.|  
|[Использование MSDeploy с поставщиком dbSqlPackage](../ssdt/using-msdeploy-with-dbsqlpackage-provider.md)|В этом разделе описывается поставщик [инструмента веб-развертывания](https://go.microsoft.com/fwlink/?LinkId=231798) с именем dbSqlPackage в составе набора SSDT, работающий со средством веб-развертывания служб Microsoft IIS (MSDeploy.exe), которое позволяет решать следующие задачи:<br /><br />– извлечение DACPAC-файла из удаленной или локальной базы данных SQL Server либо Базы данных SQL Azure;<br />– публикация DACPAC-файла в удаленной или локальной базе данных SQL Server либо Базе данных SQL Azure для ее добавочного обновления;<br />– публикация из локальной базы данных SQL Server в удаленную базу данных SQL Server или Базу данных SQL Azure для добавочного обновления удаленной базы данных;<br />– сравнение DACPAC-файла с удаленной или локальной базой данных SQL Server или Базой данных SQL Azure для создания скрипта Transact\-SQL для добавочного обновления без обновления активной базы данных;<br />– создание XML-отчета со сводкой изменений, которые будут внесены в случае добавочного обновления базы данных.|  
  
## <a name="related-sections"></a>См. также  
[Разработка базы данных вне сети с учетом проекта](../ssdt/project-oriented-offline-database-development.md)  
  

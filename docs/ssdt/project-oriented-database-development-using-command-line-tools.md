---
title: Разработка баз данных с учетом проекта при помощи программ командной строки | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 04/26/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 9a26def9-8fbd-43e4-9e57-414840b73ed8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7cf13ec0608dd3340e37307f5040172311ed7463
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65101863"
---
# <a name="project-oriented-database-development-using-command-line-tools"></a>Разработка баз, ориентированная на проекты, с помощью программ командной строки
В состав SQL Server Data Tools входят программы командной строки, при помощи которых можно реализовать ряд сценариев разработки баз данных с учетом проекта.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|||  
|-|-|  
|[SqlPackage.exe](../tools/sqlpackage.md)|В этом разделе описывается программа SQLPackage.exe, позволяющая решать следующие задачи:<br /><br />– извлечение DACPAC-файла из активной базы данных SQL Server;<br />– публикация DACPAC-файла в активной базе данных SQL Server для добавочного обновления схемы активной базы данных для соответствия с DACPAC-файлом;<br />– сравнение DACPAC-файла с активной базой данных SQL Server и создание скрипта Transact\-SQL для добавочного обновления без обновления активной базы данных;<br />– сравнение двух DACPAC-файлов для создания скрипта Transact\-SQL для добавочного обновления;<br />– создание XML-отчета со сводкой изменений, которые будут внесены в случае добавочного обновления базы данных.|  
|[Использование MSDeploy с поставщиком dbSqlPackage](../ssdt/using-msdeploy-with-dbsqlpackage-provider.md)|В этом разделе описывается поставщик [инструмента веб-развертывания](https://go.microsoft.com/fwlink/?LinkId=231798) с именем dbSqlPackage в составе набора SSDT, работающий со средством веб-развертывания служб Microsoft IIS (MSDeploy.exe), которое позволяет решать следующие задачи:<br /><br />– извлечение DACPAC-файла из удаленной или локальной базы данных SQL Server либо SQL Azure;<br />– публикация DACPAC-файла в удаленной или локальной базе данных SQL Server либо SQL Azure для ее добавочного обновления;<br />– публикация из локальной базы данных SQL Server в удаленную базу данных SQL Server или SQL Azure для добавочного обновления удаленной базы данных;<br />– сравнение DACPAC-файла с удаленной или локальной базой данных SQL Server или SQL Azure для создания скрипта Transact\-SQL для добавочного обновления без обновления активной базы данных;<br />– создание XML-отчета со сводкой изменений, которые будут внесены в случае добавочного обновления базы данных.|  
  
## <a name="related-sections"></a>См. также  
[Разработка базы данных вне сети с учетом проекта](../ssdt/project-oriented-offline-database-development.md)  
  

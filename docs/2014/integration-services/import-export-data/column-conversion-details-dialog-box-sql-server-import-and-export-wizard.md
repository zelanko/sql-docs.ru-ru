---
title: Диалоговое окно "Сведения о преобразовании столбца" (мастер импорта и экспорта SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.issuedetails.f1
ms.assetid: e2d00a39-dfbd-4821-a4d8-a5bd1164ed4d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ccdf69264de1531c1296763eb95e2e0369ce034b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48215754"
---
# <a name="column-conversion-details-dialog-box-sql-server-import-and-export-wizard"></a>Диалоговое окно «Сведения о преобразовании столбца» (мастер импорта и экспорта SQL Server)
  Используйте **сведения о преобразовании столбца** диалоговое окно, чтобы просмотреть подробные сведения о отдельного столбца преобразовании. Эти сведения содержат тип данных столбца в источнике и назначении, а также преобразование, которое будет выполнено мастером. На этой странице также перечисляются файлы сопоставления типов данных, используемые мастером для определения требуемых преобразований. Эти файлы устанавливаются в процессе установки служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 **Чтобы открыть диалоговое окно сведения о преобразовании столбца**  
  
1.  На **Просмотр проблем с типами данных** странице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] мастер импорта и экспорта, в **таблицы** выберите таблицу.  
  
2.  В **сопоставление типов данных** дважды щелкните строку, содержащую столбец, для которого требуется просмотреть сведения о преобразовании.  
  
 Дополнительные сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] мастер импорта и экспорта, см. в разделе [SQL Server Импорт и экспорт](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Дополнительные сведения о параметрах запуска этого мастера и о разрешениях, необходимых для успешного запуска мастера, см. в разделе [запустить мастер экспорта и импорта SQL Server](start-the-sql-server-import-and-export-wizard.md).  
  
 Цель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] мастер импорта и экспорта заключается в копировании данных из источника в место назначения. Этот мастер может также создать целевую базу данных и целевые таблицы. Однако если нужно скопировать несколько баз данных, таблиц или других объектов базы данных, следует использовать мастер копирования баз данных. Дополнительные сведения см. в статье [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
  

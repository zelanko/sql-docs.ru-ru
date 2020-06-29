---
title: Диалоговое окно "Сведения о преобразовании столбца" (мастер импорта и экспорта SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.issuedetails.f1
ms.assetid: e2d00a39-dfbd-4821-a4d8-a5bd1164ed4d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9207e76191060c56acad37db734827579a83aae0
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85436831"
---
# <a name="column-conversion-details-dialog-box-sql-server-import-and-export-wizard"></a>Диалоговое окно «Сведения о преобразовании столбца» (мастер импорта и экспорта SQL Server)
  Используйте диалоговое окно **сведения о преобразовании столбца** для просмотра подробных сведений о преобразовании отдельного столбца. Эти сведения содержат тип данных столбца в источнике и назначении, а также преобразование, которое будет выполнено мастером. На этой странице также перечисляются файлы сопоставления типов данных, используемые мастером для определения требуемых преобразований. Эти файлы устанавливаются в процессе установки служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 **Открытие диалогового окна «Сведения о преобразовании столбца»**  
  
1.  На странице **Просмотр проблем с типами данных** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] мастера импорта и экспорта в списке **Таблица** выберите таблицу.  
  
2.  В списке **Сопоставление типов данных** дважды щелкните строку, содержащую столбец, сведения о преобразовании которого необходимо просмотреть.  
  
 Дополнительные сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] мастере импорта и экспорта см. в разделе [SQL Server мастер импорта и экспорта](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Дополнительные сведения о параметрах запуска мастера и о разрешениях, необходимых для успешного запуска мастера, см. [в разделе Запуск мастера импорта и экспорта SQL Server](start-the-sql-server-import-and-export-wizard.md).  
  
 Мастера импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предназначен для копирования данных из исходного расположения в целевое. Этот мастер может также создать целевую базу данных и целевые таблицы. Однако если нужно скопировать несколько баз данных, таблиц или других объектов базы данных, следует использовать мастер копирования баз данных. Дополнительные сведения см. в статье [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
  

---
description: Диалоговое окно «Сохранение (запрещено)»
title: Диалоговое окно «Сохранение (запрещено)»
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.table.tablerecreatenosave.f1
ms.assetid: 7efda8e3-739f-4c97-a497-b8808a0acbea
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 868925a64b24ab7f55551a691b4677a658082725
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88369090"
---
# <a name="save-not-permitted-dialog-box"></a>Диалоговое окно «Сохранение (запрещено)»
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Диалоговое окно **Сохранение (запрещено)** выдает предупреждение о том, что сохранение невозможно, поскольку выполненные изменения требуют удаления и повторного создания перечисленных таблиц.  
  
Повторное создание таблицы может понадобиться для следующих действий:  
  
-   добавление нового столбца в середину таблицы;  
  
-   удаление столбца;  
  
-   изменение допустимости значения NULL для столбца;  
  
-   изменение порядка столбцов;  
  
-   изменение типа данных столбца.  
  
Чтобы изменить этот параметр, в меню **Сервис** выберите пункт **Параметры**, разверните **Конструкторы**и щелкните **Конструкторы таблиц и баз данных**. Установите или снимите флажок **Запретить сохранение изменений, требующих повторного создания таблицы** .  
  

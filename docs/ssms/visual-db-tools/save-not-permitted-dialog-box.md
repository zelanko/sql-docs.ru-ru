---
title: Диалоговое окно "Сохранение (запрещено)" | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.table.tablerecreatenosave.f1
ms.assetid: 7efda8e3-739f-4c97-a497-b8808a0acbea
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b491d5d0bf14c90d813b0fc66c0112eac1ff0e16
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47635302"
---
# <a name="save-not-permitted-dialog-box"></a>Диалоговое окно «Сохранение (запрещено)»
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Диалоговое окно **Сохранение (запрещено)** выдает предупреждение о том, что сохранение невозможно, поскольку выполненные изменения требуют удаления и повторного создания перечисленных таблиц.  
  
Повторное создание таблицы может понадобиться для следующих действий:  
  
-   добавление нового столбца в середину таблицы;  
  
-   удаление столбца;  
  
-   изменение допустимости значения NULL для столбца;  
  
-   изменение порядка столбцов;  
  
-   изменение типа данных столбца.  
  
Чтобы изменить этот параметр, в меню **Сервис** выберите пункт **Параметры**, разверните **Конструкторы**и щелкните **Конструкторы таблиц и баз данных**. Установите или снимите флажок **Запретить сохранение изменений, требующих повторного создания таблицы** .  
  

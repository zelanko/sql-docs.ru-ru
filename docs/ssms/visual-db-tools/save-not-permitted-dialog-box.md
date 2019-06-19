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
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e753a0854e5ac8f789249a211b4af3990417279c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65099882"
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
  

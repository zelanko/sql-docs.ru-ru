---
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
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: 9dde13a71dac042d8bf5c351cb4f9655f322acd8
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75255118"
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
  

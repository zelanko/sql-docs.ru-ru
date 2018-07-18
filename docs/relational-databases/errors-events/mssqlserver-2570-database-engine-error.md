---
title: MSSQLSERVER_2570 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 2570 (Database Engine error)
ms.assetid: 29800aa9-81aa-4371-992c-487dbb617f46
caps.latest.revision: 20
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8f6803dc02e037a114fd5c9e40da0fcc8871d8be
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
ms.locfileid: "34319156"
---
# <a name="mssqlserver2570"></a>MSSQLSERVER_2570
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|2570|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC_COLUMN_VALUE_OUT_OF_RANGE|  
|Текст сообщения|Страница P_ID, область памяти S_ID в идентификаторе объекта O_ID, идентификатор индекса I_ID, идентификатор секции PN_ID, идентификатор единицы распределения A_ID (тип TYPE). Значение столбца COLUMN_NAME вне допустимого диапазона типа данных «DATATYPE». Замените значение столбца на допустимое.|  
  
## <a name="explanation"></a>Объяснение  
Значение указанного столбца выходит за пределы допустимого диапазона возможных значений для типа данных этого столбца.  
  
## <a name="user-action"></a>Действие пользователя  
Исправить ошибку невозможно. Замените значение столбца на допустимое в пределах диапазона для типа данных этого столбца и выполните команду еще раз.  Дополнительные сведения см. в статье базы знаний [923247](http://support.microsoft.com/kb/923247).  
  
## <a name="see-also"></a>См. также:  
[UPDATE (Transact-SQL)](~/t-sql/queries/update-transact-sql.md)  
[Типы данных (Transact-SQL)](~/t-sql/data-types/data-types-transact-sql.md)  
  

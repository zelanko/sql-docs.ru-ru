---
title: MSSQLSERVER_2570 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2570 (Database Engine error)
ms.assetid: 29800aa9-81aa-4371-992c-487dbb617f46
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5169e030246b8f5a834e6a2526232907a7e22526
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53360626"
---
# <a name="mssqlserver2570"></a>MSSQLSERVER_2570
    
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
 Исправить ошибку невозможно. Замените значение столбца на допустимое в пределах диапазона для типа данных этого столбца и выполните команду еще раз.  Дополнительные сведения см. в статье базы знаний [923247](https://support.microsoft.com/kb/923247).  
  
## <a name="see-also"></a>См. также  
 [UPDATE (Transact-SQL)](/sql/t-sql/queries/update-transact-sql)   
 [Типы данных (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)  
  
  

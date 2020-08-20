---
description: MSSQLSERVER_2570
title: MSSQLSERVER_2570 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2570 (Database Engine error)
ms.assetid: 29800aa9-81aa-4371-992c-487dbb617f46
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 81a19dc1d0301fd8e098fbc45485f2318e3cd0e3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482857"
---
# <a name="mssqlserver_2570"></a>MSSQLSERVER_2570
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|2570|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC_COLUMN_VALUE_OUT_OF_RANGE|  
|Текст сообщения|Страница P_ID, область памяти S_ID в идентификаторе объекта O_ID, идентификатор индекса I_ID, идентификатор секции PN_ID, идентификатор единицы распределения A_ID (тип TYPE). Значение столбца COLUMN_NAME вне допустимого диапазона типа данных «DATATYPE». Замените значение столбца на допустимое.|  
  
## <a name="explanation"></a>Объяснение  
Значение указанного столбца выходит за пределы допустимого диапазона возможных значений для типа данных этого столбца.  
  
## <a name="user-action"></a>Действие пользователя  
Исправить ошибку невозможно. Замените значение столбца на допустимое в пределах диапазона для типа данных этого столбца и выполните команду еще раз.  Дополнительные сведения см. в статье базы знаний [923247](https://support.microsoft.com/kb/923247).  
  
## <a name="see-also"></a>См. также:  
[UPDATE (Transact-SQL)](~/t-sql/queries/update-transact-sql.md)  
[Типы данных (Transact-SQL)](~/t-sql/data-types/data-types-transact-sql.md)  
  

---
title: MSSQLSERVER_7711 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7711 (Database Engine error)
ms.assetid: a5c7cd6e-18d6-47ef-902b-db9dd64bba34
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ef193b4089a1ef92bd28877feb95902eee5bbc42
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551089"
---
# <a name="mssqlserver_7711"></a>MSSQLSERVER_7711
    
## <a name="details"></a>Сведения  
  
|attribute|Значение|  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|7711|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PRT_RANGE_OVERLAP|  
|Текст сообщения|Параметр DATA_COMPRESSION указан более одного раза для таблицы, индекса, либо одной из секций таблицы или индекса.|  
  
## <a name="explanation"></a>Объяснение  
 В одной из следующих инструкций при обработке параметра DATA_COMPRESSION произошла ошибка.  
  
-   CREATE TABLE  
  
-   ALTER TABLE  
  
-   CREATE INDEX  
  
-   ALTER INDEX  
  
 Если указанная таблица (или индекс) секционирована, то по крайней мере для одной из секций параметр DATA_COMPRESSION был указан более одного раза. Если указанная таблица (или индекс) не секционирована, то параметр DATA_COMPRESSION был указан более одного раза.  
  
## <a name="user-action"></a>Действие пользователя  
 Применительно к секционированной таблице (индексу) убедитесь, что параметр DATA_COMPRESSION указан для каждой секции не более одного раза. Применительно к несекционированной таблице (индексу), указывайте параметр DATA_COMPRESSION в этой инструкции не более одного раза.  
  
  

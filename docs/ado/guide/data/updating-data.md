---
title: "Обновление данных | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data updates [ADO], about data updates
- updating data [ADO], about updating data
ms.assetid: 6508e4e9-e33a-4dad-b340-5d632fd78a91
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c8138aeea7e5ea40e659a6fed5f5d5f551b1c69d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="updating-data"></a>Обновление данных
Обновление поведения и функциональных возможностей во многом зависит от обновления режима (тип блокировки), тип курсора и положения курсора.  
  
 Используйте **обновление** метод, чтобы сохранить любые изменения, внесенные в текущую запись **набора записей** объект с момента вызова **AddNew** метода или с момента изменять любые значения полей в существующей записи. **Записей** объект должен поддерживать обновлений.  
  
 Если **записей** объект поддерживает обновление пакета, можно кэшировать внесение нескольких изменений в одну или несколько записей локально до вызова **UpdateBatch** метод. При изменении текущей записи или добавления новой записи, при вызове **UpdateBatch** метода ADO будет автоматически вызывать **обновление** метод, чтобы сохранить все ожидающие изменения для текущей записи, прежде чем передает пакет изменений к поставщику.  
  
 Текущая запись остаются актуальными, после вызова метода **обновление** или **UpdateBatch** методы.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Режима интерпретации](../../../ado/guide/data/immediate-mode.md)  
  
-   [Пакетный режим](../../../ado/guide/data/batch-mode.md)  
  
-   [Обработка транзакций](../../../ado/guide/data/transaction-processing.md)


---
title: Обновление данных | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data updates [ADO], about data updates
- updating data [ADO], about updating data
ms.assetid: 6508e4e9-e33a-4dad-b340-5d632fd78a91
author: rothja
ms.author: jroth
ms.openlocfilehash: 26f3ca9220ea41db43b9f98a12429dcb5874bba4
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82750226"
---
# <a name="updating-data"></a>Обновление данных
Поведение и функциональность обновления во многом зависят от режима обновления (типа блокировки), типа курсора и положения курсора.  
  
 Используйте метод **Update** , чтобы сохранить изменения, внесенные в текущую запись объекта **Recordset** с момента вызова метода **AddNew** или путем изменения любых значений полей в существующей записи. Объект **набора записей** должен поддерживать обновления.  
  
 Если объект **Recordset** поддерживает пакетное обновление, можно кэшировать несколько изменений в одной или нескольких записях локально, пока не будет вызван метод **UpdateBatch** . Если вы изменяете текущую запись или добавляете новую запись при вызове метода **UpdateBatch** , ADO автоматически вызывает метод **Update** , чтобы сохранить все ожидающие изменения в текущей записи перед передачей пакетных изменений поставщику.  
  
 Текущая запись остается текущей после вызова методов **Update** или **UpdateBatch** .  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Режим интерпретации](../../../ado/guide/data/immediate-mode.md)  
  
-   [Пакетный режим](../../../ado/guide/data/batch-mode.md)  
  
-   [Обработка транзакций](../../../ado/guide/data/transaction-processing.md)

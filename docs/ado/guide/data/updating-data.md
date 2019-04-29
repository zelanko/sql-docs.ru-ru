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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d593bd3ad745f316b833b375ceaae8b764d21ec2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63184985"
---
# <a name="updating-data"></a>Обновление данных
Поведение обновления и функции во многом зависит от обновления режима (тип блокировки), тип курсора и положения курсора.  
  
 Используйте **обновление** метод, чтобы сохранить любые изменения, внесенные в текущую запись **записей** объекта с момента вызова **AddNew** метод или после изменения значения поля в существующей записи. **Записей** объект должен поддерживать обновления.  
  
 Если **записей** объект поддерживает обновление пакета, внесение нескольких изменений в одну или несколько записей можно кэшировать локально до вызова метода **UpdateBatch** метод. При изменении текущей записи или добавления новой записи, при вызове **UpdateBatch** метод, автоматически вызывает ADO **обновления** метод для сохранения любых ожидающих изменений в текущую запись, прежде чем передает пакет изменений к поставщику.  
  
 Текущая запись остается текущее, после вызова метода **обновление** или **UpdateBatch** методы.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Режим интерпретации](../../../ado/guide/data/immediate-mode.md)  
  
-   [Пакетный режим](../../../ado/guide/data/batch-mode.md)  
  
-   [Обработка транзакций](../../../ado/guide/data/transaction-processing.md)

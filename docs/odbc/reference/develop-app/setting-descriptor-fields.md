---
title: Задание полей дескриптора | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: d735dc64-370f-48ab-a59f-6cef9bc4e1e8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fc02690bd62802f9d356851cd85522328107a707
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="setting-descriptor-fields"></a>Задание полей дескриптора
Чтобы изменить поля дескриптора, приложение может вызвать **SQLSetDescField**. Некоторые поля доступны только для чтения и не может быть задано. (См. [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) описание функции.)  
  
 Поля дескриптора записи устанавливаются с помощью номер записи (*RecNumber*) из 1 или более поздней версии, пока поля заголовка дескриптора устанавливаются с помощью число записей в 0. Число записей в 0 используется также для полей закладки, в соответствии с соглашением, что закладки содержатся в столбце 0. Это может привести впечатление, что поля закладки содержащиеся в заголовке дескриптора, но это не так. Закладка полей отличаются от полей заголовка.  
  
 При задании поля по отдельности, приложения должны соответствовать последовательности, определенной в [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). При указании некоторых полей драйвер установить другие поля. Это гарантирует, что дескриптор будет готов к использованию сразу же приложение указанный тип данных. Когда приложение задает поле SQL_DESC_TYPE, драйвер проверяет наличие других полей, которые определяют тип правильны и согласуются.  
  
 При сбое вызова функции, указывающую поле дескриптора значения поля дескриптора не определены после вызова функции, завершившейся сбоем.

---
title: "Задание полей дескриптора | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: d735dc64-370f-48ab-a59f-6cef9bc4e1e8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f4e63f722842846815fd96bed7293388c4f86c75
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setting-descriptor-fields"></a>Задание полей дескриптора
Чтобы изменить поля дескриптора, приложение может вызвать **SQLSetDescField**. Некоторые поля доступны только для чтения и не может быть задано. (См. [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) описание функции.)  
  
 Поля дескриптора записи устанавливаются с помощью номер записи (*RecNumber*) из 1 или более поздней версии, пока поля заголовка дескриптора устанавливаются с помощью число записей в 0. Число записей в 0 используется также для полей закладки, в соответствии с соглашением, что закладки содержатся в столбце 0. Это может привести впечатление, что поля закладки содержащиеся в заголовке дескриптора, но это не так. Закладка полей отличаются от полей заголовка.  
  
 При задании поля по отдельности, приложения должны соответствовать последовательности, определенной в [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). При указании некоторых полей драйвер установить другие поля. Это гарантирует, что дескриптор будет готов к использованию сразу же приложение указанный тип данных. Когда приложение задает поле SQL_DESC_TYPE, драйвер проверяет наличие других полей, которые определяют тип правильны и согласуются.  
  
 При сбое вызова функции, указывающую поле дескриптора значения поля дескриптора не определены после вызова функции, завершившейся сбоем.

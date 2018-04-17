---
title: Задание полей дескриптора | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
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
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0ceadd4fd1474c934ff147290761d9cb99a4089b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="setting-descriptor-fields"></a>Задание полей дескриптора
Чтобы изменить поля дескриптора, приложение может вызвать **SQLSetDescField**. Некоторые поля доступны только для чтения и не может быть задано. (См. [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) описание функции.)  
  
 Поля дескриптора записи устанавливаются с помощью номер записи (*RecNumber*) из 1 или более поздней версии, пока поля заголовка дескриптора устанавливаются с помощью число записей в 0. Число записей в 0 используется также для полей закладки, в соответствии с соглашением, что закладки содержатся в столбце 0. Это может привести впечатление, что поля закладки содержащиеся в заголовке дескриптора, но это не так. Закладка полей отличаются от полей заголовка.  
  
 При задании поля по отдельности, приложения должны соответствовать последовательности, определенной в [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). При указании некоторых полей драйвер установить другие поля. Это гарантирует, что дескриптор будет готов к использованию сразу же приложение указанный тип данных. Когда приложение задает поле SQL_DESC_TYPE, драйвер проверяет наличие других полей, которые определяют тип правильны и согласуются.  
  
 При сбое вызова функции, указывающую поле дескриптора значения поля дескриптора не определены после вызова функции, завершившейся сбоем.

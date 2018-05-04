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
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: d735dc64-370f-48ab-a59f-6cef9bc4e1e8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5ea00d83f1f57498ee1094264c1895f50103526c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="setting-descriptor-fields"></a>Задание полей дескриптора
Чтобы изменить поля дескриптора, приложение может вызвать **SQLSetDescField**. Некоторые поля доступны только для чтения и не может быть задано. (См. [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) описание функции.)  
  
 Поля дескриптора записи устанавливаются с помощью номер записи (*RecNumber*) из 1 или более поздней версии, пока поля заголовка дескриптора устанавливаются с помощью число записей в 0. Число записей в 0 используется также для полей закладки, в соответствии с соглашением, что закладки содержатся в столбце 0. Это может привести впечатление, что поля закладки содержащиеся в заголовке дескриптора, но это не так. Закладка полей отличаются от полей заголовка.  
  
 При задании поля по отдельности, приложения должны соответствовать последовательности, определенной в [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). При указании некоторых полей драйвер установить другие поля. Это гарантирует, что дескриптор будет готов к использованию сразу же приложение указанный тип данных. Когда приложение задает поле SQL_DESC_TYPE, драйвер проверяет наличие других полей, которые определяют тип правильны и согласуются.  
  
 При сбое вызова функции, указывающую поле дескриптора значения поля дескриптора не определены после вызова функции, завершившейся сбоем.

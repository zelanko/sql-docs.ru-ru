---
title: Драйверы Unicode Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], drivers
- Unicode [ODBC], functions
- functions [ODBC], Unicode functions
ms.assetid: 3b4742d5-74fb-4aff-aa21-d83a0064d73d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: aabdd899d78c1141716725d57e343dc002dc96ad
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284356"
---
# <a name="unicode-drivers"></a>Драйверы Юникода
Должен ли драйвер Unicode быть или драйвер ANSI полностью зависит от характера источника данных. Если источник данных поддерживает данные Unicode, драйвером должен быть драйвер Unicode. Если источник данных поддерживает только данные ANSI, драйвер должен оставаться драйвером ANSI.  
  
 Драйвер Unicode должен экспортировать **S'LConnectW,** чтобы быть признанным драйвером Unicode менеджером драйвера.  
  
 Водитель Unicode должен принимать функции Unicode (с суффиксом *W)* и хранить данные Unicode. Он также может принимать функции ANSI, но не требуется. (Менеджер драйвера не передает водителю вызов функции ANSI с суффиксом *А,* но преобразует его в вызов функции ANSI без суффикса, а затем передает его водителю.)  
  
 Драйвер Unicode должен иметь возможность возвращать наборы результатов в Unicode или ANSI, в зависимости от связывания приложения. Если приложение привязывается к SQL_C_CHAR, драйвер Unicode должен преобразовать данные SQL_WCHAR в SQL_CHAR. Менеджер драйверов будет отображать SQL_C_WCHAR SQL_C_CHAR для драйверов ANSI, но не делает отображение для драйверов Unicode.  
  
> [!NOTE]  
>  При определении типа драйвера менеджер драйвера вызовет **S'LSetConnectAttr** и установит SQL_ATTR_ANSI_APP атрибут во время соединения. Если приложение использует API ANSI, SQL_ATTR_ANSI_APP будет установлен на SQL_AA_TRUE, а если оно использует Unicode, то оно будет установлено на SQL_AA_FALSE. Этот атрибут используется таким образом, что драйвер может проявлять различное поведение в зависимости от типа приложения. Атрибут не может быть установлен приложением напрямую, и он не поддерживается **S'LGetConnectAttr.** Если драйвер демонстрирует одинаковое поведение как для приложений ANSI, так и для Unicode, он должен вернуть SQL_ERROR для этого атрибута. Если водитель возвращается SQL_SUCCESS, менеджер драйвера будет отделять соединения ANSI и Unicode при использовании пулинга соединения.

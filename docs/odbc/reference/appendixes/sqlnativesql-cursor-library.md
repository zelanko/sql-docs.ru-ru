---
title: SQLNativeSql (библиотека курсоров) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLNativeSql function [ODBC], Cursor Library
ms.assetid: c4459092-1177-4b2a-b7f5-e0083d3bf2b2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c5b87f64963e7b0ad45fbec33e410165cd0c9723
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47656714"
---
# <a name="sqlnativesql-cursor-library"></a>SQLNativeSql (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональные возможности драйвера курсора.  
  
 В этом разделе рассматривается использование **SQLNativeSql** функции в библиотеку курсоров. Общие сведения о **SQLNativeSql**, см. в разделе [функция SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md).  
  
 Если драйвер поддерживает эту функцию, вызывает библиотеку курсоров **SQLNativeSql** в драйвере и передает его в инструкции SQL. Для позиционированного обновления расположен delete, и **ВЫБЕРИТЕ для обновления** инструкций, библиотека курсоров изменяет инструкцию перед их передачей драйвер.  
  
> [!NOTE]  
>  Библиотека курсоров неправильно возвращает SQLSTATE 34000 (недопустимое имя курсора), если имя курсора является недопустимым в выполнении позиционированного обновления или инструкцию delete, которая передается в *InStatementText* аргумент **SQLNativeSql** . **SQLNativeSql** не предназначен для возврата синтаксических ошибок, которые возвращаются только при подготовке инструкции или выполнения.

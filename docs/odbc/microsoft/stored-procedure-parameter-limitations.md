---
title: Ограничения параметров процедуры сохранены (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 8b804bcf-4cce-4e6f-aa45-00bab9ef9921
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bbd748884575791d5f170e95bc5aa465b61624b7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299204"
---
# <a name="stored-procedure-parameter-limitations"></a>Ограничения параметров хранимой процедуры
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставленный Oracle.  
  
 При запуске процедур Oracle, хранящихся с использованием 10 или более выходных параметров, вызов сохраненной процедуры завершится неудачей, что приведет к ошибке объектов данных Доступа или ActiveX Data Objects (ADO). Это может произойти при использовании Драйвера Microsoft ODBC для Oracle с версиями 8.0.4.0.0 и 8.0.4.0.4 программного обеспечения клиента Oracle.  
  
 Чтобы исправить проблему, клиентское программное обеспечение Oracle должно быть обновлено до версии 8.0.4.2.0 или выше. Свяжитесь с корпорацией Oracle для получения дополнительной информации о [патчах.](../../odbc/microsoft/oracle-software-patches.md)  
  
> [!NOTE]  
>  Эта проблема не возникает с ранним выпуском версии программного обеспечения клиента Oracle 8.0.0.0.

---
title: Тестирование подключения ODBC (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- testing connections [ODBC]
- ODBC driver for Oracle [ODBC], testing connections
ms.assetid: 5e671665-2aba-49a7-8871-70784d8b3cc9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8de19af2b50a58eef22ec074a308f86717278a48
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303115"
---
# <a name="testing-the-odbc-connection"></a>Тестирование подключения ODBC
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставленный Oracle.  
  
 При устранении неполадок доступа ODBC к серверам Oracle 7.x и Oracle8 RDBMS может потребоваться убедиться в правильной установке базовых адаптеров протокола S'L-Net и Oracle. Для этого используйте утилиту Nettest.exe, поставляемую Oracle, в каталоге Orawin-Bin.  
  
 Nettest — это простая утилита, которая пытается войти на выбранный сервер, используя только установленное программное обеспечение S'L-Net, которое является частью клиента Oracle. Утилита запросит имя входа, пароль и строку подключения TNS. Если клиент Oracle правильно установлен, утилита будет просто отображать "Пинг Успешный". Если логин не был успешным, вам нужно проконсультироваться с администратором базы данных.

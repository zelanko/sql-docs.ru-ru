---
title: Многопоточные приложения | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- threads [SQL Server], multithreaded applications
- ODBC applications, multithreaded applications
- asynchronous operations [SQL Server Native Client]
- SQL Server Native Client ODBC driver, multithreaded applications
- multithreaded applications [SQL Server Native Client]
ms.assetid: d352c91a-6e08-4e50-9f3e-a37892d9c2cc
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 994e5dcd70d1df0dffd2c11a0a2bb7091351e20c
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40394754"
---
# <a name="multithreaded-applications"></a>Многопоточные приложения
  Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] является многопоточным драйвером. Написание многопоточного приложения — альтернатива использованию асинхронных вызовов для обработки нескольких вызовов ODBC. Поток может выполнить асинхронный вызов ODBC, а другие потоки могут обрабатываться, пока первый поток ожидает ответа на свой вызов. Эта модель эффективнее по сравнению с асинхронными вызовами, поскольку исключает такие издержки, как сетевой трафик и повторные вызовы функций ODBC с целью проверки значения SQL_STILL_EXECUTING.  
  
 Асинхронный режим все же остается эффективным методом обработки. Выигрыш в производительности многопоточной модели недостаточен, чтобы стала оправданной переработка асинхронных приложений. Если пользователям приходится преобразовывать приложения DB-Library, в которых используется асинхронная модель DB-Library, то проще преобразовать их в асинхронную модель ODBC.  
  
## <a name="see-also"></a>См. также  
 [Создание драйвера ODBC для собственного клиента SQL Server](creating-a-driver-application.md)  
  
  

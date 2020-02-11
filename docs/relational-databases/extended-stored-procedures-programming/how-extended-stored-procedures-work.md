---
title: Как работают расширенные хранимые процедуры | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], about extended stored procedures
ms.assetid: 6e946d8c-3268-4b59-8a1c-1637909cd701
author: rothja
ms.author: jroth
ms.openlocfilehash: 42aad667b6081e79b4b7897d4dd1f354a6148e8b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "72904042"
---
# <a name="how-extended-stored-procedures-work"></a>Принципы работы расширенных хранимых процедур

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Вместо этого используйте интеграцию со средой CLR.  
  
 Принцип работы расширенной хранимой процедуры заключается в следующем.  
  
1.  Когда клиент выполняет расширенную хранимую процедуру, запрос передается в виде потока табличных данных (TDS) или в формате протокола SOAP из клиентского приложения в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ищет DLL-библиотеки, связанные с расширенной хранимой процедурой, и загружает их, если они еще не загружены.  
  
3.  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вызывает запрошенную расширенную хранимую процедуру (реализованную как функцию внутри DLL-библиотеки).  
  
4.  Расширенная хранимая процедура передает результирующий набор и возвращает параметры обратно на сервер через API-интерфейс расширенной хранимой процедуры.  


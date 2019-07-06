---
title: Принципы работы расширенных хранимых процедур | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: f7bbc9fad964f5d58efeb48683b052275f7fb166
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/05/2019
ms.locfileid: "67583324"
---
# <a name="how-extended-stored-procedures-work"></a>Принципы работы расширенных хранимых процедур

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Пользуйтесь вместо этого интеграцией со средой CLR.  
  
 Принцип работы расширенной хранимой процедуры заключается в следующем.  
  
1.  Когда клиент выполняет расширенную хранимую процедуру, запрос передается в поток табличных данных (TDS) или формате Simple Object Access Protocol (SOAP) из клиентского приложения к [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ищет DLL-библиотеки, связанные с расширенной хранимой процедурой, и загружает их, если они еще не загружены.  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вызывает запрошенную расширенную хранимую процедуру (реализованную как функцию внутри DLL-библиотеки).  
  
4.  Расширенная хранимая процедура передает результирующий набор и возвращает параметры обратно на сервер через API-интерфейс расширенной хранимой процедуры.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]


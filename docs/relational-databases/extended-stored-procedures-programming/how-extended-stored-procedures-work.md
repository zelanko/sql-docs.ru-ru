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
ms.openlocfilehash: ab0864e8eb320c63bd757d4c6edab384c6c821b8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62742240"
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

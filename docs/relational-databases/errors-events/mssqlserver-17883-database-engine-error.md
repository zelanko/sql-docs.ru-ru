---
title: MSSQLSERVER_17883 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17883 (Database Engine error)
ms.assetid: adaf1c04-e397-4a69-90b8-9353a37277ea
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b4f79f4b9e6b71656f0c9ff8751c41d5b9437afa
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68137219"
---
# <a name="mssqlserver_17883"></a>MSSQLSERVER_17883
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17883|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SRV_SCHEDULER_NONYIELDING|  
|Текст сообщения|Процесс %ld:%ld:%ld (0x%lx) Worker 0x%p, по-видимому, не возвращает управление планировщику %ld. Время создания потока: %I64d. Примерная загрузка ЦП для потока: ядро %I64d мс, пользователь %I64d мс. Эффективность использования процесса %d%%. Бездействие системы %d%%. Интервал: %I64d мс.|  
  
## <a name="explanation"></a>Объяснение  
Указывает на возможную проблему, в результате которой поток не возвращает управление планировщику.  Возможно, это сбой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] либо [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не получает достаточно циклов процессора для выполнения.  Эта ошибка может исчезнуть, если поток, в конце концов, передаст управление.  
  
## <a name="user-action"></a>Действие пользователя  
В случае избыточной нагрузки на систему уменьшите ее. В противном случае обратитесь в службу поддержки пользователей Майкрософт.  
  

---
title: MSSQLSERVER_8443 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8443 (Database Engine error)
ms.assetid: a3541b9c-b1a8-4280-add1-275f08696b62
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 23d53cad26ed52d985fa5c99fe07c9f0dd64e42f
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68101514"
---
# <a name="mssqlserver_8443"></a>MSSQLSERVER_8443
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|8443|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SB_DIALOG_WO_CONV_GROUP|  
|Текст сообщения|Диалог с идентификатором "%.*ls" и инициатором %d указывает на несуществующую группу сообщений "%.\*ls". Запустите DBCC CHECKDB для анализа и восстановления базы данных.|  
  
## <a name="explanation"></a>Объяснение  
Для группы сообщений слой метаданных возвратил значение NULL. База данных каким-то образом повреждена. Одним из возможных источников повреждений является ошибка жесткого диска.  
  
## <a name="user-action"></a>Действие пользователя  
Запустите DBCC CHECKDB в режиме исправлений для восстановления базы данных до согласованного состояния. При восстановлении согласованности возможно удаление сообщений. Изучите журналы ошибок системы, чтобы понять, не возникла ли эта ошибка в результате другой неисправности в системе.  
  

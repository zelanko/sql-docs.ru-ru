---
title: MSSQLSERVER_8443 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8443 (Database Engine error)
ms.assetid: a3541b9c-b1a8-4280-add1-275f08696b62
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bf8060645d7bc6cbfdb9af76f1035a86810aa16b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62867174"
---
# <a name="mssqlserver8443"></a>MSSQLSERVER_8443
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|8443|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SB_DIALOG_WO_CONV_GROUP|  
|Текст сообщения|Диалог с идентификатором "%.*ls" и инициатором %d указывает на несуществующую группу сообщений "%.\*ls". Запустите DBCC CHECKDB для анализа и восстановления базы данных.|  
  
## <a name="explanation"></a>Объяснение  
 Для группы сообщений слой метаданных возвратил значение NULL. База данных каким-то образом повреждена. Одним из возможных источников повреждений является ошибка жесткого диска.  
  
## <a name="user-action"></a>Действие пользователя  
 Запустите DBCC CHECKDB в режиме исправлений для восстановления базы данных до согласованного состояния. При восстановлении согласованности возможно удаление сообщений. Изучите журналы ошибок системы, чтобы понять, не возникла ли эта ошибка в результате другой неисправности в системе.  
  
  

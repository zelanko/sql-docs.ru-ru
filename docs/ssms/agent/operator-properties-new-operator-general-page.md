---
title: Свойства оператора — создание оператора (страница "Общие") | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.ag.operator.general.f1
ms.assetid: c036d1c9-83d1-4a95-b67e-29d283b1a046
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5c85048f2e5fb02fd060d3c813b1b4cdbc23d637
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="operator-properties---new-operator-general-page"></a>Свойства оператора — создание оператора (страница "Общие")
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Используйте эту страницу для просмотра и изменения общих свойств операторов агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
## <a name="options"></a>Параметры  
**Название**  
Изменить имя оператора.  
  
**Enabled**  
Разрешить оператор. Если он не включен, то уведомления оператору не отправляются.  
  
**Имя для электронной почты**  
Определяет адрес электронной почты оператора.  
  
**Адрес для команды net send**  
Задает адрес, используемый для **net send**.  
  
**Имя для сообщения на пейджер**  
Определяет адрес электронной почты пейджера оператора.  
  
**Расписание работы для пейджера**  
Указывает время, когда пейджер активен.  
  
**Понедельник — воскресенье**  
Выберите дни, когда пейджер активен.  
  
**Начало рабочего дня**  
Выберите время суток, после которого агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] отправляет сообщения на пейджер.  
  
**Конец рабочего дня**  
Выберите время суток, после которого агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] перестает отправлять сообщения на пейджер.  
  
## <a name="see-also"></a>См. также:  
[Операторы](../../ssms/agent/operators.md)  
  

---
title: Свойства созданного оператора (страница "Общие")
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.operator.general.f1
ms.assetid: c036d1c9-83d1-4a95-b67e-29d283b1a046
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 73aa6081584ef3ae99206808631abc05e4674bae
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75247661"
---
# <a name="operator-properties---new-operator-general-page"></a>Свойства оператора — создание оператора (страница "Общие")

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Используйте эту страницу для просмотра и изменения общих свойств операторов агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="options"></a>Параметры  
**имя**;  
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
Выберите время суток, после которого агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отправляет сообщения на пейджер.  
  
**Конец рабочего дня**  
Выберите время суток, после которого агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перестает отправлять сообщения на пейджер.  
  
## <a name="see-also"></a>См. также:  
[Операторы](../../ssms/agent/operators.md)  
  

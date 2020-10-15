---
description: Свойства учетной записи-посредника — создание учетной записи-посредника (страница "Общие")
title: Свойства учетной записи-посредника — создание учетной записи-посредника (страница "Общие")
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.proxy.general.f1
ms.assetid: 5cd81265-bf59-413b-8397-150ddc70d0c7
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a70ba36150771ef90f3cfc9461c018c212da4c73
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92037309"
---
# <a name="proxy-account-properties---new-proxy-account-general-page"></a>Свойства учетной записи-посредника — создание учетной записи-посредника (страница "Общие")
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Используйте эту страницу для просмотра и изменения свойств учетной записи-посредника для агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="options"></a>Параметры  
**Имя учетной записи-посредника**  
Введите имя учетной записи-посредника.  
  
**Имя учетных данных**  
Введите учетное имя для учетной записи-посредника.  
  
> [!NOTE]  
> Необходимо ввести реально существующие учетное имя. Сведения о создании учетных данных см. в разделе [Как создать прокси-сервер](../../relational-databases/security/authentication-access/create-a-credential.md)  
  
**...**  
Открывает диалоговое окно **Выбор учетных данных** .  
  
**Описание**  
Введите описание учетной записи-посредника.  
  
**Активна для следующих подсистем**  
Выберите подсистемы, к которым учетная запись-посредник будет иметь доступ.  
  
**Повторно присвоить шаги заданий**  
Выберите учетную запись-посредник, которой следует повторно присвоить шаги задания. Этот список активен при отмене доступа к подсистеме, к которой ранее был доступ у учетной записи-посредника.  
  
## <a name="see-also"></a>См. также:  
[Создание учетной записи-посредника агента SQL Server](../../ssms/agent/create-a-sql-server-agent-proxy.md)  

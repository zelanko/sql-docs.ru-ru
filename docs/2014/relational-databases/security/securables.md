---
title: Защищаемые объекты | Документация Майкрософт
ms.custom: ''
ms.date: 10/14/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.roleproperties.selectobject.f1
helpviewer_keywords:
- securables [SQL Server]
- schemas [SQL Server], securables
- database securables [SQL Server]
- hierarchies [SQL Server], securables
- server securables [SQL Server]
ms.assetid: bfa748f0-70b0-453c-870a-04b7b205b9ff
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 7c4a82cfa4d8a82db1e01c49899c3c49c2e01ee9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62745723"
---
# <a name="securables"></a>Защищаемые объекты
  К защищаемым объектами относятся ресурсы, доступ к которым регулируется системой авторизации компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Например, защищаемым объектом является таблица. Некоторые защищаемые объекты могут храниться внутри других, создавая иерархии «областей», которые сами могут защищаться. К областям защищаемых объектов относятся **сервер**, **база данных**и **схема**.  
  
## <a name="securable-scope-server"></a>Область защищаемых объектов: сервер  
 Область защищаемых объектов **сервера** содержит следующие защищаемые объекты:  
  
-   группа доступности  
  
-   Конечная точка  
  
-   Имя входа  
  
-   Роль сервера  
  
-   База данных  
  
## <a name="securable-scope-database"></a>Область защищаемых объектов: база данных  
 Область защищаемых объектов **базы данных** содержит следующие защищаемые объекты:  
  
-   Роль приложения  
  
-   Сборка  
  
-   Асимметричный ключ  
  
-   Сертификат  
  
-   Контракт  
  
-   Полнотекстовый каталог  
  
-   Полнотекстовый список стоп-слов  
  
-   тип сообщений;  
  
-   Привязка удаленной службы  
  
-   Роль (база данных)  
  
-   Маршрут  
  
-   схема  
  
-   Поиск в списке свойств  
  
-   Служба  
  
-   Симметричный ключ  
  
-   Пользователь  
  
## <a name="securable-scope-schema"></a>Область защищаемых объектов: схема  
 Область защищаемых объектов **схемы** содержит следующие защищаемые объекты:  
  
-   Тип  
  
-   Коллекция схем XML  
  
-   Объект — к классу объекта относятся следующие элементы:  
  
    -   Статистическое  
  
    -   Компонент  
  
    -   Процедура  
  
    -   Очередь  
  
    -   Синоним  
  
    -   Таблица  
  
    -   Представление  
  
## <a name="controlling-access-to-a-securable"></a>Управление доступом к защищаемому объекту  
 Сущность, которая получает разрешение на доступ к защищаемому объекту, именуется участником. Наиболее часто в роли участников выступают имена входа и пользователи базы данных. Управление доступом к защищаемым объектам осуществляется путем предоставления или отзыва разрешений либо путем добавления имен входа и пользователей к ролям, имеющим доступ. Сведения об управлении разрешениями см. в разделах [GRANT (Transact-SQL)](/sql/t-sql/statements/grant-transact-sql), [REVOKE (Transact-SQL)](/sql/t-sql/statements/revoke-transact-sql), [DENY (Transact-SQL)](/sql/t-sql/statements/deny-transact-sql), [Хранимая процедура sp_addrolemember (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) и [sp_droprolemember (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql).  
  
> [!CAUTION]  
>  Разрешения по умолчанию, которые предоставляются системным объектам во время установки, тщательно оцениваются на предмет возможных угроз, и их не нужно будет изменять для защиты установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Любые изменения разрешений в системных объектах могут ограничить или нарушить функциональность, а также перевести установку [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в неподдерживаемое состояние.  
  
## <a name="related-content"></a>См. также  
 [Обеспечение безопасности SQL Server](securing-sql-server.md)  
  
 [sys. database_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-principals-transact-sql)  
  
 [sys. database_role_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-role-members-transact-sql)  
  
 [sys. server_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql)  
  
 [sys. server_role_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-role-members-transact-sql)  
  
 [sys. sql_logins &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-logins-transact-sql)  
  
  

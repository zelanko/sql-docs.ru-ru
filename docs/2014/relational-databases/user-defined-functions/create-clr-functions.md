---
title: Создание функций CLR | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- CLR functions [SQL Server]
- user-defined functions [SQL Server], CLR
ms.assetid: a82df075-2243-4e19-bfe1-ae6d65dabd0f
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 1a15690eb5aff48ec0f72df16e8342ed5c0522c9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62524064"
---
# <a name="create-clr-functions"></a>Создание функций CLR
  В экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно создать объект базы данных, который запрограммирован в сборке, созданной в среде CLR платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] . К объектам базы данных, способным обогатить возможности применения многофункциональной модели программирования среды CLR, относятся агрегатные функции, функции, хранимые процедуры, триггеры и типы.  
  
 Чтобы создать функцию CLR в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , необходимо выполнить следующие шаги:  
  
-   Определить функцию как статический метод класса на языке, поддерживаемом [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Дополнительные сведения о программировании функций в среде CLR см. в разделе [Определяемые пользователем функции среды CLR](../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md). После этого следует скомпилировать класс для создания сборки в платформе [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] , с помощью компилятора соответствующего языка.  
  
-   Зарегистрируйте эту сборку в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью инструкции CREATE ASSEMBLY. Дополнительные сведения о работе со сборками в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Сборки (компонент Database Engine)](../clr-integration/assemblies-database-engine.md).  
  
-   Создать функцию, ссылающуюся на зарегистрированную сборку, с помощью инструкции [CREATE FUNCTION](/sql/t-sql/statements/create-function-transact-sql) .  
  
> [!NOTE]  
>  Развертывание проекта SQL Server в [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] регистрирует сборку в базе данных, указанной для проекта. Кроме того, в базе данных создаются функции CLR для всех методов, сопровождаемых атрибутом `SqlFunction`. Дополнительные сведения см. в статье [Deploying CLR Database Objects](../clr-integration/deploying-clr-database-objects.md).  
  
> [!NOTE]  
>  Возможность [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнять код CLR по умолчанию отключена. Можно создавать, изменять и удалять объекты базы данных, которые ссылаются на модули управляемого кода, но эти ссылки не будут выполнены в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , пока не будет включен параметр [clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) с помощью процедуры [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).  
  
## <a name="accessing-external-resources"></a>Доступ к внешним ресурсам  
 Функции CLR могут использоваться для доступа к внешним ресурсам, например файлам, сетевым ресурсам, веб-службам, другим базам данных (в том числе и удаленным экземплярам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). Этого можно достичь, используя различные классы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], например `System.IO`, `System.WebServices`, `System.Sql`и другие. Сборка, содержащая такие функции, должна иметь как минимум разрешения EXTERNAL_ACCESS, чтобы иметь доступ к внешним ресурсам. Дополнительные сведения см. в статье [CREATE ASSEMBLY (Transact-SQL)](/sql/t-sql/statements/create-assembly-transact-sql). Для доступа к удаленным экземплярам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]можно использовать управляемый поставщик клиента SQL (SQL Client Managed Provider). Однако замыкание соединений на сервер-источник в функциях CLR не поддерживается.  
  
 **Создание, изменение и удаление сборок в SQL Server**  
  
-   [CREATE ASSEMBLY (Transact-SQL)](/sql/t-sql/statements/create-assembly-transact-sql)  
  
-   [ALTER ASSEMBLY (Transact-SQL)](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
-   [DROP ASSEMBLY (Transact-SQL)](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 **Создание функции CLR**  
  
-   [CREATE FUNCTION (Transact-SQL)](/sql/t-sql/statements/create-function-transact-sql)  
  
## <a name="accessing-native-code"></a>Доступ к машинному коду  
 Функции CLR можно использовать для доступа к собственному (неуправляемому) коду, например написанному на C или C++, посредством использования средства PInvoke из управляемого кода (подробнее см. в разделе [Вызов собственных функций из управляемого кода](https://go.microsoft.com/fwlink/?LinkID=181929) ). Это даст возможность повторно использовать устаревший код в виде определяемых пользователем функций CLR или писать критичные к производительности функции в собственном коде. Для этого потребуется использование сборки UNSAFE. Предупреждения, касающиеся использования сборок UNSAFE, см. в разделе [CLR Integration Code Access Security](../clr-integration/security/clr-integration-code-access-security.md) .  
  
## <a name="see-also"></a>См. также  
 [Создание определяемых пользователем функций (компонент Database Engine)](create-user-defined-functions-database-engine.md)   
 [Создание определяемых пользователем агрегатных функций](create-user-defined-aggregates.md)   
 [Выполнение определяемых пользователем функций](execute-user-defined-functions.md)   
 [Просмотр определяемых пользователем функций](view-user-defined-functions.md)   
 [Основные понятия о программировании интеграции со средой (CLR)](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  

---
title: Создание функций CLR | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: udf
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- CLR functions [SQL Server]
- user-defined functions [SQL Server], CLR
ms.assetid: a82df075-2243-4e19-bfe1-ae6d65dabd0f
caps.latest.revision: 34
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8c2c74068c438cb5284cc8ae5bd92f91100662e4
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37419493"
---
# <a name="create-clr-functions"></a>Создание функций CLR
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  В экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно создать объект базы данных, который запрограммирован в сборке, созданной в среде CLR платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] . К объектам базы данных, способным обогатить возможности применения многофункциональной модели программирования среды CLR, относятся агрегатные функции, функции, хранимые процедуры, триггеры и типы.  
  
 Чтобы создать функцию CLR в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , необходимо выполнить следующие шаги:  
  
-   Определить функцию как статический метод класса на языке, поддерживаемом [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Дополнительные сведения о программировании функций в среде CLR см. в разделе [Определяемые пользователем функции среды CLR](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md). После этого следует скомпилировать класс для создания сборки в платформе [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] , с помощью компилятора соответствующего языка.  
  
-   Зарегистрируйте эту сборку в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью инструкции CREATE ASSEMBLY. Дополнительные сведения о работе со сборками в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Сборки (компонент Database Engine)](../../relational-databases/clr-integration/assemblies-database-engine.md).  
  
-   Создать функцию, ссылающуюся на зарегистрированную сборку, с помощью инструкции [CREATE FUNCTION](../../t-sql/statements/create-function-transact-sql.md) .  
  
> [!NOTE]  
>  Развертывание проекта SQL Server в [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] регистрирует сборку в базе данных, указанной для проекта. Кроме того, в базе данных создаются функции CLR для всех методов, сопровождаемых атрибутом **SqlFunction** . Дополнительные сведения см. в статье [Deploying CLR Database Objects](../../relational-databases/clr-integration/deploying-clr-database-objects.md).  
  
> [!NOTE]  
>  Возможность [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнять код CLR по умолчанию отключена. Можно создавать, изменять и удалять объекты базы данных, которые ссылаются на модули управляемого кода, но эти ссылки не будут выполнены в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , пока не будет включен параметр [clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) с помощью процедуры [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
## <a name="accessing-external-resources"></a>Доступ к внешним ресурсам  
 Функции CLR могут использоваться для доступа к внешним ресурсам, например файлам, сетевым ресурсам, веб-службам, другим базам данных (в том числе и удаленным экземплярам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). Этого можно достичь, используя различные классы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], например `System.IO`, `System.WebServices`, `System.Sql`и другие. Сборка, содержащая такие функции, должна иметь как минимум разрешения EXTERNAL_ACCESS, чтобы иметь доступ к внешним ресурсам. Дополнительные сведения см. в статье [CREATE ASSEMBLY (Transact-SQL)](../../t-sql/statements/create-assembly-transact-sql.md). Для доступа к удаленным экземплярам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]можно использовать управляемый поставщик клиента SQL (SQL Client Managed Provider). Однако замыкание соединений на сервер-источник в функциях CLR не поддерживается.  
  
 **Создание, изменение и удаление сборок в SQL Server**  
  
-   [CREATE ASSEMBLY (Transact-SQL)](../../t-sql/statements/create-assembly-transact-sql.md)  
  
-   [ALTER ASSEMBLY (Transact-SQL)](../../t-sql/statements/alter-assembly-transact-sql.md)  
  
-   [DROP ASSEMBLY (Transact-SQL)](../../t-sql/statements/drop-assembly-transact-sql.md)  
  
 **Создание функции CLR**  
  
-   [CREATE FUNCTION (Transact-SQL)](../../t-sql/statements/create-function-transact-sql.md)  
  
## <a name="accessing-native-code"></a>Доступ к машинному коду  
 Функции CLR можно использовать для доступа к собственному (неуправляемому) коду, например написанному на C или C++, посредством использования средства PInvoke из управляемого кода (подробнее см. в разделе [Вызов собственных функций из управляемого кода](http://go.microsoft.com/fwlink/?LinkID=181929) ). Это даст возможность повторно использовать устаревший код в виде определяемых пользователем функций CLR или писать критичные к производительности функции в собственном коде. Для этого потребуется использование сборки UNSAFE. Предупреждения, касающиеся использования сборок UNSAFE, см. в разделе [CLR Integration Code Access Security](../../relational-databases/clr-integration/security/clr-integration-code-access-security.md) .  
  
## <a name="see-also"></a>См. также:  
 [Создание определяемых пользователем функций (компонент Database Engine)](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md)   
 [Создание определяемых пользователем агрегатных функций](../../relational-databases/user-defined-functions/create-user-defined-aggregates.md)   
 [Выполнение определяемых пользователем функций](../../relational-databases/user-defined-functions/execute-user-defined-functions.md)   
 [Просмотр определяемых пользователем функций](../../relational-databases/user-defined-functions/view-user-defined-functions.md)   
 [Основные понятия о программировании интеграции со средой (CLR)](../../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  

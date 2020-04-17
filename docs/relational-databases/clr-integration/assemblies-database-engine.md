---
title: Сборки (Движуки баз данных) Документы Майкрософт
description: Экземпляр S'L Server может размещать сборки, развертывающие функции, процедуры, триггеры и пользовательские агрегаты и типы, написанные на языке CLR.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration]
- assemblies [CLR integration], about assemblies
- managed code [SQL Server], assemblies
ms.assetid: 4b146437-3061-47f6-9e8c-26eeea10b54e
author: rothja
ms.author: jroth
ms.openlocfilehash: 386e1980ae19ba4f98222b51a4955b024f815083
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488085"
---
# <a name="assemblies-database-engine"></a>Сборки (компонент Database Engine)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе содержатся сведения, которые помогут понять, сконструировать и применить сборки.  
  
 Сборки — это DLL-файлы, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используемые в экземпляре для развертывания функций, сохраненных процедур, триггеров, пользовательских агрегатов и [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] пользовательских типов, написанных на [!INCLUDE[tsql](../../includes/tsql-md.md)]одном из управляемых языков кода, размещенных общим временем выполнения языка (CLR), а не в.  
  
 Сборка в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] представляет собой объект, который ссылается на управляемый модуль приложений (DLL-файл), созданный в среде CLR [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Сборка содержит метаданные класса и управляемый код. Передача сборки на экземпляр SQL Server — это первый шаг к созданию любого из следующих объектов базы данных.  
  
-   Функции среды CLR. Для получения дополнительной информации [см.](../../relational-databases/user-defined-functions/create-clr-functions.md)  
  
-   Хранимые процедуры среды CLR. Для получения дополнительной информации [см.](https://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33)  
  
-   Триггеры среды CLR. Для получения дополнительной [информации см.](../../relational-databases/triggers/create-clr-triggers.md)  
  
-   Определяемые пользователем агрегатные функции. Для получения дополнительной [информации см.](../../relational-databases/user-defined-functions/create-user-defined-aggregates.md)  
  
-   Определяемые пользователем типы. Дополнительные сведения см. в статье [Использование пользовательских типов](../../relational-databases/native-client/features/using-user-defined-types.md).  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сборки выполняют следующие функции.  
  
-   Содержат управляемый код, который выполняет функциональность одного или нескольких объектов базы данных среды CLR, перечисленных ранее.  
  
-   Содержат метаданные, которые включают в себя номер версии и культуру сборки, дополнительный открытый ключ, который уникально идентифицирует список классов сборки, методы, определенные в сборке, и архитектуру процессора сборки.  
  
-   Управляют степенью, к которой управляемый код может получить доступ внешних ресурсов с помощью регулирования разрешений кода доступа.  
  
-   Содержат метаданные о зависимостях от других сборок, на которые ссылается сборка.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Конструирование сборок](../../relational-databases/clr-integration/assemblies-designing.md)|Объясняет, что необходимо учесть перед созданием сборки. Включает в себя упаковку сборок, разрешения кода доступа и другие ограничения.|  
|[Реализация сборок](../../relational-databases/clr-integration/assemblies-implementing.md)|Объясняет, как правильно создать и удалить сборку, как и когда необходимо изменить сборку, а также как получить метаданные о сборке.|  
|[Получение сведений о сборках](../../relational-databases/clr-integration/assemblies-getting-information.md)|Перечисляет представления и функции каталога, которые могут запрашиваться для метаданных о сборках.|  
  
## <a name="see-also"></a>См. также:  
 [Основные понятия о программировании интеграции со средой (CLR)](../../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  

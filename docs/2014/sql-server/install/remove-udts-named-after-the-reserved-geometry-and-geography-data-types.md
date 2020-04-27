---
title: Удалите определяемые пользователем типы, названные после зарезервированных геометрических и географических типов данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- geometry data type [SQL Server], UDTs
- geography data type [SQL Server], UDTs
ms.assetid: a167ce3a-50b4-4e77-a884-adb23b586c72
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b5e7b5ed9d730eb51e9994a8bd068eefda9715a5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66092936"
---
# <a name="remove-udts-named-after-the-reserved-geometry-and-geography-data-types"></a>Удалите определяемые пользователем типы с именами, совпадающими с зарезервированными типами данных GEOMETRY и GEOGRAPHY
  Помощник по обновлению обнаружил определяемый пользователем тип, имя которого совпадает с именем, зарезервированным для типа данных `geometry` или `geography`. Типы данных `geometry` и `geography` являются частью компонента для обработки пространственных данных.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Имена терминов, используемых в типах пространственных данных, не должны использоваться в качестве имен определяемых пользователем типов среды CLR или их псевдонимов.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Удалите определяемый пользователем тип и создайте его повторно с именем, отличным от зарезервированного.  
  
## <a name="external-resources"></a>Внешние ресурсы  
 [Создание определяемого пользователем типа](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
 [Основные сведения о типах пространственных данных](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  

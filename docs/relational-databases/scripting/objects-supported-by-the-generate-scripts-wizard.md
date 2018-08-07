---
title: Объекты, поддерживаемые мастером создания скриптов | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 6c9c94a2060bcabe012162074bb05ff2fd8fc261
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39539754"
---
# <a name="objects-supported-by-the-generate-scripts-wizard"></a>Объекты, поддерживаемые мастером создания скриптов
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Мастер создания и публикации скриптов поддерживает подмножество объектов, поддерживаемое компонентом [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
## <a name="supported-objects"></a>Поддерживаемые объекты  
 В следующей таблице перечислены объекты, которые можно публиковать при поддержке мастера формирования и публикации скриптов.  
  
||||||  
|-|-|-|-|-|  
|роль приложения;|Роль базы данных|Схема|Определяемое пользователем статистическое выражение|Представление*|  
|Сборка|Ограничение DEFAULT|Хранимая процедура*|Определяемый пользователем тип данных|Коллекция схем XML|  
|Ограничение CHECK|Полнотекстовый каталог|Синоним|Определяемая пользователем функция||  
|Хранимая процедура среды CLR*|Указатель|Таблица|Определяемая пользователем таблица||  
|Определяемая пользователем функция CLR|Правило|Пользователь**|Определяемый пользователем тип||  
  
 *Опубликовано без шифрования.  
  
 **Все несистемные пользователи, существующие в базе данных, будут опубликованы как роли.  
  
  

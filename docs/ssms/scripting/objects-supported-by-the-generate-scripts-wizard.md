---
title: Объекты, поддерживаемые мастером создания скриптов | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 35882207de5528147883ed3ebe408344cbd3f7fc
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/14/2018
ms.locfileid: "51644000"
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
  
  

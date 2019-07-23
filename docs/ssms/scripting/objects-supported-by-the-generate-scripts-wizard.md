---
title: Объекты, поддерживаемые мастером создания скриптов | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c9b1a48c19ad6e6b0e33d2b7f0d9ad326d866e00
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68262276"
---
# <a name="objects-supported-by-the-generate-scripts-wizard"></a>Объекты, поддерживаемые мастером создания скриптов
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Мастер создания и публикации скриптов поддерживает подмножество объектов, поддерживаемое компонентом [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
## <a name="supported-objects"></a>Поддерживаемые объекты  
 В следующей таблице перечислены объекты, которые можно публиковать при поддержке мастера формирования и публикации скриптов.  
  
||||||  
|-|-|-|-|-|  
|Роль приложения|Роль базы данных|схема|Определяемое пользователем статистическое выражение|Представление*|  
|Сборка|Ограничение DEFAULT|Хранимая процедура*|Определяемый пользователем тип данных|Коллекция схем XML|  
|Ограничение CHECK|Полнотекстовый каталог|Синоним|Определяемая пользователем функция||  
|Хранимая процедура среды CLR*|Указатель|Таблица|Определяемая пользователем таблица||  
|Определяемая пользователем функция CLR|Правило|Пользователь**|Определяемый пользователем тип||  
  
 *Опубликовано без шифрования.  
  
 **Все несистемные пользователи, существующие в базе данных, будут опубликованы как роли.  
  
  

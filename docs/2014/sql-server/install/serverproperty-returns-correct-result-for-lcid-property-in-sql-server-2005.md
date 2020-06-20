---
title: SERVERPROPERTY возвращает правильный результат для свойства LCID в SQL Server 2005 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SERVERPROPERTY function
ms.assetid: 833a2fc9-b480-4697-aa7b-9677e78ee0b4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ebb125a86e6e30f2c3638004593da7657f02f1a6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85036466"
---
# <a name="serverproperty-returns-correct-result-for-lcid-property-in-sql-server-2005"></a>В SQL Server 2005 функция SERVERPROPERTY возвращает правильный результат для свойства LCID
  При выполнении функции SERVERPROPERTY('LCID') на серверах с параметрами двоичной сортировки эта функция возвращает значение LCID, соответствующее параметрам сортировки сервера.  
  
> [!NOTE]  
>  Для пакетных файлов и файлов трассировки, использующих функцию SERVERPROPERTY ('LCID') и запускаемых на других экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], помощник по обновлению обнаружит это изменение в поведении, только если параметры сортировки у других экземпляров и текущего экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] совпадают.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Следует изменить приложения, чтобы они ожидали от функции SERVERPROPERTY('LCID') возвращения кода языка Windows, соответствующего параметрам сортировки сервера.  
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  

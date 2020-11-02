---
description: MSSQLSERVER_17112
title: MSSQLSERVER_17112
ms.custom: ''
ms.date: 08/20/2020
ms.prod: sql
ms.reviewer: ramakoni1, pijocoder, suresh-kandoth, Masha
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17112 (Database Engine error)
ms.assetid: ''
author: suresh-kandoth
ms.author: ramakoni
ms.openlocfilehash: 870f9b9f4d3fcc8186ed1d16faee861ed63e4135
ms.sourcegitcommit: ead0b8c334d487a07e41256ce5d6acafa2d23c9d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2020
ms.locfileid: "92418802"
---
# <a name="mssqlserver_17112"></a>MSSQLSERVER_17112
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

## <a name="details"></a>Сведения

|attribute|Значение|
|---|---|
|Название продукта|SQL Server|
|Идентификатор события|17112|
|Источник события|MSSQLSERVER|
|Компонент|SQLEngine|
|Символическое имя|INIT_INVCOMMAND|
|Текст сообщения|В реестре или в командной строке указан неверный параметр запуска a. Исправьте или удалите параметр.|
||

## <a name="explanation"></a>Пояснение

Эта ошибка означает, что заданы недопустимые [параметры запуска службы "Ядро СУБД"](/sql/database-engine/configure-windows/database-engine-service-startup-options). Если параметр запуска указан неверно, SQL Server либо может не запуститься, либо будет работать непредсказуемым образом. Также возникает ошибка 17112.

В некоторых случаях экземпляр может запуститься, но при просмотре журнала ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметры запуска будут выглядеть неправильно:

> \<Datetime> Сервер. Параметры запуска в реестре:  
\<Datetime> Сервер. -d D:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\DATA\master.mdf  
\<Datetime> Сервер. -e D:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\LOG\ERRORLOG  
\<Datetime> Сервер. -l D:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\DATA\mastlog.ldf  
\<Datetime> Сервер. -T1118 -g512

Обратите внимание на то, что два последних параметра запуска находятся в одной строке.

Кроме того, в некоторых случаях добавление необходимых параметров запуска влияет на работу сервера не так, как ожидалось.

## <a name="possible-causes"></a>Возможные причины

Эти проблемы возникают по следующим причинам:

- использование параметров запуска, которых нет в списке допустимых;
- указание параметров запуска без соответствующих разделителей (;);
- копирование и вставка параметров запуска из текстовых редакторов, в которых добавляются невидимые специальные символы (например, пробел перед -T);
- использование неправильного регистра символов в параметре запуска.

## <a name="user-action"></a>Рекомендуемые действия

С помощью средства [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager задайте и проверьте параметры запуска для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Убедитесь в том, что все параметры запуска правильно разделены и в них нет специальных символов.

## <a name="more-information"></a>Дополнительные сведения

Дополнительные сведения по этой теме см. в следующих статьях:

- [Параметры запуска службы Database Engine](/sql/database-engine/configure-windows/database-engine-service-startup-options)
- [Службы SCM. Настройка параметров запуска сервера](/sql/database-engine/configure-windows/scm-services-configure-server-startup-options)

---
title: SQL Server Migration Assistant для Access (AccessToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 08/14/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 40c1eb02-26b2-44ba-969d-6c430c61c281
caps.latest.revision: 22
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: 3ffc062101434178ba5739c553508202d6b73c6a
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2018
ms.locfileid: "38985606"
---
# <a name="sql-server-migration-assistant-for-access-accesstosql"></a>SQL Server Migration Assistant для Access (AccessToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) для доступа — это средство для переноса баз данных из [!INCLUDE[msCoName](../../includes/msconame_md.md)] доступ к версиям 97 до 2010 к [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005 / [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 / [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 / [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 / [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 / [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2017 в Windows и Linux (Предварительная версия) / [!INCLUDE[msCoName](../../includes/msconame_md.md)] база данных Azure SQL. SSMA для Access преобразует объекты базы данных доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или объекты базы данных Azure SQL, загружает эти объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или Azure SQL, и затем переносит данные из доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или Azure SQL.  
  
В этой документации представлены SSMA для Access и приведены пошаговые инструкции по миграции баз данных для доступа к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure и сведения о проблемах, которые могут возникнуть после миграции.  
  
## <a name="contents"></a>Содержание  
  
|Раздел|Описание|  
|-----------|---------------|  
|[Новые возможности в SSMA для Access](http://msdn.microsoft.com/a24d3fc0-6911-4bfa-828a-197abf222e02)|Список всех изменений к выпускам SSMA.|  
|[Установка SQL Server Migration Assistant для Access](http://msdn.microsoft.com/dd50eebd-75df-4e0d-8c4d-88b511aae4c7)|Предварительные требования для установки SSMA, процедура установки и лицензирования SSMA и ссылку на последнюю версию.|  
|[Приступая к работе с SQL Server Migration Assistant для Access &#40;AccessToSQL&#41;](../../ssma/access/getting-started-with-sql-server-migration-assistant-for-access-accesstosql.md)|Знакомство с SSMA и его пользовательский интерфейс.|  
|[Подготовка к миграции базы данных Access](http://msdn.microsoft.com/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)|Описывается подготовка базы данных Access для преобразования в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SQL Azure.|  
|[Миграция баз данных Access в SQL Server](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)|Обзор процесса преобразования и подробные сведения о каждом шаге в процессе.|  
|[Связь приложений Access SQL Server](http://msdn.microsoft.com/82374ad2-7737-4164-a489-13261ba393d4)|Описывается, как использовать существующие приложения Access с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|[Справочник по пользовательскому интерфейсу](http://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)|Содержит документацию по SSMA диалоговым окнам.|  
|[Работа с консолью SSMA для Access](http://msdn.microsoft.com/ef94e843-9f88-45a2-86c4-a0af268738c4)|Содержит документацию по SSMA консольного приложения|  
|[Получение поддержки по SSMA для Access](http://go.microsoft.com/fwlink/?LinkID=708538&clcid=0x409)|Сведения о получении дополнительной помощи.|  
  

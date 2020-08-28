---
description: Методы службы удаленных рабочих столов
title: Методы RDS | Документация Майкрософт
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
helpviewer_keywords:
- RDS methods [ADO]
- methods [ADO], RDS
ms.assetid: c2c6af1a-3c44-4c9d-ad33-b381552c71af
author: rothja
ms.author: jroth
ms.openlocfilehash: 8403881e3e25f612ac9a27a798ad2d88f192d5cd
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88981645"
---
# <a name="rds-methods"></a>Методы службы удаленных рабочих столов
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
|Метод|Описание|  
|-|-|  
|[Отмена (RDS)](./cancel-method-rds.md)|Отменяет выполнение ожидающего асинхронного вызова метода.|  
|[CancelUpdate (RDS)](./cancelupdate-method-rds.md)|Отменяет все изменения, внесенные в текущую или новую строку объекта **набора записей** .|  
|[ConvertToString (RDS)](./converttostring-method-rds.md)|Преобразует **набор записей** в строку MIME, представляющую данные набора записей.|  
|[CreateObject (RDS)](./createobject-method-rds.md)|Создает прокси-сервер для целевого бизнес-объекта и возвращает указатель на него.|  
|[CreateRecordset (RDS)](./createrecordset-method-rds.md)|Создает пустой, отключенный **набор записей**.|  
|[Метод Execute (служба удаленных рабочих столов)](./execute-method-rds.md)|Выполните запрос и создайте расширенный набор строк данных (для использования с ADO 2,5 и более поздних версий).|  
|[Метод Execute21 (служба удаленных рабочих столов)](./execute21-method-rds.md)|Выполните запрос и создайте расширенный набор строк данных (для использования с ADO 2,1).|  
|[InvokeService (служба удаленных рабочих столов)](./invokeservice-rds.md)|Возвращает указатель на запрошенный интерфейс в более совместимой версии объекта.|  
|[MoveFirst, MoveLast, MoveNext, MovePrevious (RDS)](./movefirst-movelast-movenext-and-moveprevious-methods-rds.md)|Переход к первой, последней, следующей или предыдущей записи в указанном объекте **набора записей** .|  
|[Запрос (RDS)](./query-method-rds.md)|Использует допустимую строку SQL-запроса для возврата **набора записей**.|  
|[Обновление (RDS)](./refresh-method-rds.md)|Повторно запрашивает источник данных, указанный в свойстве **Connect** , и обновляет результаты запроса.|  
|[Сброс (RDS)](./reset-method-rds.md)|Выполняет сортировку или фильтрацию в **наборе записей**на стороне клиента на основе указанных свойств сортировки и фильтра.|  
|[SubmitChanges (RDS)](./submitchanges-method-rds.md)|Отправляет ожидающие изменения локально кэшированного и обновляемого **набора записей** в источник данных, указанный в свойстве **Connect** .|  
|[Метод Synchronize (служба удаленных рабочих столов)](./synchronize-method-rds.md)|Синхронизирует заданный набор записей с базой данных, указанной в строке подключения (для использования с ADO 2,5 и более поздними версиями).|  
|[Метод Synchronize21 (служба удаленных рабочих столов)](./synchronize21-method-rds.md)|Синхронизирует заданный набор записей с базой данных, указанной в строке подключения (для использования с ADO 2,1).|
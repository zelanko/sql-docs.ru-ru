---
title: Контекстное соединение | Документация Майкрософт
description: В Microsoft SQL Server контекстное соединение позволяет выполнять инструкции Transact-SQL в том же контексте, в котором был вызван код.
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context connections [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- context [CLR integration]
ms.assetid: 67dd1925-d672-4986-a85f-bce4fe832ef7
author: rothja
ms.author: jroth
ms.openlocfilehash: cd0b57e73757348959a0b8b5f144fbc5c4ef0f8c
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892474"
---
# <a name="context-connection"></a>Контекстное соединение
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Проблема внутреннего доступа к данным встречается довольно часто. Речь идет о тех ситуациях, когда необходимо получить доступ к тому же серверу, на котором выполняется конкретная хранимая процедура или функция среды CLR. Один из вариантов — создать соединение с помощью **System. Data. SqlClient. SqlConnection**, указать строку подключения, указывающую на локальный сервер, и открыть соединение. В этом случае требуется указать учетные данные для входа в систему. Соединение находится в другом сеансе базы данных, чем хранимая процедура или функция, он может иметь разные параметры **Set** , он находится в отдельной транзакции, не увидит временные таблицы и т. д. Если управляемая хранимая процедура или функция выполняется в процессе SQL Server, причина этого состоит в том, что кто-то соединился с этим сервером и выполнил инструкцию SQL для вызова соответствующего процедуры или функции. Возможно, вам нужно, чтобы хранимая процедура или функция выполнялась в контексте этого соединения, а также его транзакции, параметров **Set** и т. д. В этом состоит так называемое контекстное соединение.  
  
 Контекстное соединение позволяет выполнять инструкции Transact-SQL в том же контексте, в каком первоначально был вызван конкретный код. Для получения контекстного соединения необходимо использовать ключевое слово «context connection» строки соединения, как в примере ниже:  
  
 [C#]  
  
```  
using(SqlConnection connection = new SqlConnection("context connection=true"))   
{  
    connection.Open();  
    // Use the connection  
}  
```  
  
 [Visual Basic]  
  
```  
Using connection as new SqlConnection("context connection=true")  
    connection.Open()  
    ' Use the connection  
End Using  
  
```  
  
## <a name="in-this-section"></a>В этом разделе  
 [Обычные и Контекстные соединения](../../../relational-databases/clr-integration/data-access/context-connections-vs-regular-connections.md)  
 Описывает разницу между регулярными и контекстными соединениями.  
  
 [Ограничения обычных и контекстных соединений](../../../relational-databases/clr-integration/data-access/context-connections-and-regular-connections-restrictions.md)  
 Описывает ограничения регулярных и контекстных соединений.  
  
  

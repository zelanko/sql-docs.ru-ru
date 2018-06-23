---
title: Контекстное соединение | Документы Microsoft
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a95f4c4b190f37674290588714fc3e7b0c6582a5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189541"
---
# <a name="context-connection"></a>Контекстное соединение
  Проблема внутреннего доступа к данным встречается довольно часто. Речь идет о тех ситуациях, когда необходимо получить доступ к тому же серверу, на котором выполняется конкретная хранимая процедура или функция среды CLR. Один из вариантов состоит в том, чтобы создать соединение с использованием `System.Data.SqlClient.SqlConnection`, задать строку соединения, в которой указан локальный сервер, и открыть соединение. В этом случае требуется указать учетные данные для входа в систему. Кроме того, соединение устанавливается в другом сеансе базы данных, отличном от сеанса хранимой процедуры или функции, поэтому оно может иметь другие параметры `SET`, находится в отдельной транзакции, не позволяет обращаться к используемым временным таблицам и т. д. Если управляемая хранимая процедура или функция выполняется в процессе SQL Server, причина этого состоит в том, что кто-то соединился с этим сервером и выполнил инструкцию SQL для вызова соответствующего процедуры или функции. В этой ситуации наверняка следует обеспечить выполнение хранимой процедуры или функции в контексте данного соединения вместе с осуществляемыми в нем транзакцией, параметрами `SET` и т. д. В этом состоит так называемое контекстное соединение.  
  
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
  
## <a name="in-this-section"></a>в этом разделе  
 [Сравнение обычных и контекстных подключений](context-connections-vs-regular-connections.md)  
 Описывает разницу между регулярными и контекстными соединениями.  
  
 [Ограничения обычных и контекстных подключений](context-connections-and-regular-connections-restrictions.md)  
 Описывает ограничения регулярных и контекстных соединений.  
  
  
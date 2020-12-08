---
title: Получение одного значения из базы данных
description: Узнайте, как получить одно значение в ADO.NET. В этом примере кода возвращается значение из столбца идентификаторов для вставленной записи.
ms.date: 11/25/2020
dev_langs:
- csharp
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: c4815d048e5648e2c89c2cc32b8f159cc515f2b5
ms.sourcegitcommit: debaff72dbfae91b303f0acd42dd6d99e03135a2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96428293"
---
# <a name="obtaining-a-single-value-from-a-database"></a>Получение одного значения из базы данных

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Может возникнуть необходимость вернуть сведения из базы данных, которые представляют собой одиночное значение, а не форму таблицы или поток данных. Допустим, может потребоваться вернуть результат агрегатной функции, например COUNT(\*), SUM(Price) или AVG(Quantity). Объект **Command** предоставляет возможность возвращать одиночные значения с помощью метода **ExecuteScalar**. Метод **ExecuteScalar** возвращает значение первого столбца первой строки результирующего набора в виде скалярного значения.

## <a name="example"></a>Пример

В следующем примере кода в базу данных при помощи <xref:Microsoft.Data.SqlClient.SqlCommand> вставляется новое значение. Метод <xref:Microsoft.Data.SqlClient.SqlCommand.ExecuteScalar%2A> используется, чтобы вернуть значение столбца идентификатора для вставленной записи.

[!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](~/../sqlclient/doc/samples/SqlCommand_ExecuteScalar_Return_Id.cs#1)]

## <a name="see-also"></a>См. также

- [Команды и параметры](commands-parameters.md)
- [Выполнение команды](execute-command.md)

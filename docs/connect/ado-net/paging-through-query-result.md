---
title: Разбивка на страницы результатов запроса
description: Предоставляет пример просмотра результатов запроса в виде страниц данных.
ms.date: 11/30/2020
dev_langs:
- csharp
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 2de305e1069964f2d1a67b7f201578c7448d3e09
ms.sourcegitcommit: c127c0752e84cccd38a7e23ac74c0362a40f952e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/07/2020
ms.locfileid: "96772281"
---
# <a name="paging-through-a-query-result"></a>Разбивка на страницы результатов запроса

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Постраничный просмотр результатов запроса - это процесс возврата результатов запроса небольшими подмножествами данных (страницами). Этот метод часто используется для вывода результатов пользователю в виде небольших фрагментов, с которыми легко работать.

Класс <xref:Microsoft.Data.SqlClient.SqlDataAdapter> предоставляет возможность возврата одной страницы данных при помощи перегрузок метода <xref:System.Data.Common.DbDataAdapter.Fill%2A>. Однако это может быть не лучшим решением для постраничного просмотра большого числа результатов запроса. Хотя класс **DataAdapter** заполняет целевые объекты <xref:System.Data.DataTable> или <xref:System.Data.DataSet> только запрошенными записями, при этом все равно используются ресурсы, необходимые для возврата всех результатов запроса.

Для возврата страницы данных из источника данных без использования лишних ресурсов задайте для запроса дополнительные критерии, которые ограничат число возвращаемых строки только необходимыми.

Чтобы использовать метод <xref:System.Data.Common.DbDataAdapter.Fill%2A> для возврата страницы данных, укажите с помощью параметра **startRecord** первую запись на странице данных, а с помощью параметра **maxRecords** — число записей на странице данных.

## <a name="example"></a>Пример

В следующем примере кода показано, как использовать метод <xref:System.Data.Common.DbDataAdapter.Fill%2A> для возврата первой страницы результатов запроса, где размер страницы — пять записей.

[!code-csharp[SqlDataAdapter_Paging#1](~/../sqlclient/doc/samples/SqlDataAdapter_Paging.cs#1)]

В предыдущем примере **DataSet** заполняется только пятью записями, но возвращается вся таблица **Orders**. Чтобы заполнить **DataSet** теми же пятью записями и возвратить только пять записей, в инструкции SQL используйте предложения `TOP` и `WHERE`, как в следующем примере кода.

[!code-csharp[SqlDataAdapter_Paging#2](~/../sqlclient/doc/samples/SqlDataAdapter_Paging.cs#2)]

> [!NOTE]
> При такой разбивке результатов запроса на странице необходимо сохранить `unique identifier`, который упорядочивает строки, чтобы передать уникальный идентификатор команде для возврата следующей страницы записей, как показано в следующем примере кода.

[!code-csharp[SqlDataAdapter_Paging#4](~/../sqlclient/doc/samples/SqlDataAdapter_Paging.cs#4)]

Чтобы возвратить `next page of records`, используя перегрузку метода **Fill**, который принимает параметры **startRecord** и **maxRecords**, следует увеличить позицию текущей записи на размер страницы и заполнить таблицу.

> [!NOTE]
> Следует помнить, что сервер базы данных возвращает все результаты запроса, даже если к **DataSet** добавляется только одна страница записей.

В следующем примере кода строки таблицы очищаются, а затем заполняются следующей страницей данных. Может быть необходимым сохранить определенное число возвращенных строк в локальном кэше, чтобы уменьшить число обращений к серверу базы данных.

[!code-csharp[SqlDataAdapter_Paging#3](~/../sqlclient/doc/samples/SqlDataAdapter_Paging.cs#3)]

Чтобы возвратить следующую страницу записей, не заставляя сервер баз данных возвращать сразу все результаты запроса, укажите ограничивающие критерии для инструкции SELECT. Так как код предыдущего примера сохранил последнюю возвращенную запись, ее можно использовать в предложении WHERE, чтобы указать для запроса начальную точку, как показано в следующем примере кода.

[!code-csharp[SqlDataAdapter_Paging#5](~/../sqlclient/doc/samples/SqlDataAdapter_Paging.cs#5)]

## <a name="see-also"></a>См. также

- [Объекты DataAdapter и DataReader](dataadapters-datareaders.md)
- [Microsoft ADO.NET для SQL Server](microsoft-ado-net-sql-server.md)

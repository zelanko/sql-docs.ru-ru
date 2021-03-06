---
title: Числа с плавающей запятой
description: Сведения о некоторых проблемах, возникающих при работе с числами с плавающей запятой в поставщике данных Microsoft SqlClient для SQL Server.
ms.date: 11/13/2020
ms.assetid: 73c218c6-1c44-4402-a167-4f6262629a91
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 12c9255e0f05d338d1c5cbe88019a9f288e4e8a5
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96126449"
---
# <a name="floating-point-numbers"></a>Числа с плавающей запятой

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

В этом разделе описаны некоторые проблемы, с которыми часто сталкиваются разработчики при работе с числами с плавающей запятой в поставщике данных Microsoft SqlClient для SQL Server. Эти проблемы связаны со способом, которым эти числа хранятся в компьютерах, и не характерны для определенных поставщиков, например <xref:Microsoft.Data.SqlClient>.

Числа с плавающей запятой, как правило, не имеют точного двоичного представления. Вместо этого в компьютере сохраняется приближение числа. В разное время для представления числа может использоваться разное число двоичных цифр. При преобразовании числа с плавающей запятой из одного представления в другое наименее значительные цифры этого числа могут немного отличаться. Обычно преобразование происходит при приведении числа из одного типа в другой. При выполнении преобразования между типами, представляющими значения базы данных, или между типами базы данных происходит отклонение. Вследствие этих изменений числа, которые логически равны, могут отличаться своими наименее значительными цифрами, что приводит к отличию между их значениями. Количество разрядов точности в числе может быть больше или меньше ожидаемого. При форматировании в виде строки число может не отображать ожидаемое значение.

Для минимизации этих эффектов необходимо использовать ближайшее соответствие между доступными числовыми типами. Например, при работе с SQL Server точное числовое значение может меняться при преобразовании значения Transact-SQL типа real в значение типа float. В .NET Framework преобразование <xref:System.Single> в <xref:System.Double> может привести к непредвиденным результатам. В обоих случаях хорошей стратегией является обеспечение использования всеми значениями приложения одинакового числового типа. Также можно использовать десятичный тип с фиксированной точностью или приводить числа с плавающей запятой к этому типу перед работой с ними.

Чтобы обойти проблемы со сравнением на равенство, рассмотрите использование кодирования приложения, чтобы отклонения в наименее значительных разрядах не учитывались. Например, вместо сравнения двух чисел - вычитать одно из другого. Если разница лежит в пределах допустимого поля округлений, то приложение рассматривает числа как одинаковые.

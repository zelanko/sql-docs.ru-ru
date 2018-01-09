---
title: "Средства R, входящий в состав программы установки SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c04ae30-d391-4369-9742-d2b275e14c0d
caps.latest.revision: "9"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: b45c1a9c58ede0342953caae58c3bd6822501c24
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="r-tools-included-with-sql-server-setup"></a>Средства R, входящий в состав программы установки SQL Server

Если вы устанавливаете R с SQL Server, вы получаете те же средства R, которые устанавливаются вместе с любой **базового** установки r, например RGui, Rterm и т. д. Поэтому с технической точки зрения, у вас все средства, необходимые для разработки и тестирования кода R.

В этом разделе перечислены средства, включенные в установку.

> [!TIP]
> 
> Обычно это упрощает отладку и тестирование кода R с помощью среды разработки выделенный. Вам будет проще выполнять код R в SQL Server, если вы тестируете его заранее из внешнего средства, чтобы можно было читать подробные сообщения об ошибках и отладки решения.
> 
> См. в этой статье список инструментов, которые можно использовать для разработки решений R и настройке их для работы с SQL Server: [Настройка клиента обработки и анализа данных](set-up-a-data-science-client.md)

**Применяется к:** служб R SQL Server 2016 (в базе данных) и Microsoft R Server (изолированный); SQL Server 2017 г машинного обучения службы (в базе данных) и машинного обучения Server (изолированный)

## <a name="r-tools-included-with-installation"></a>Средства R, входящий в состав установки

Следующие стандартные средства R включены в *базовые установки* r и поэтому устанавливаются по умолчанию.

+ **RTerm**: терминал командной строки для выполнения скриптов R

+ **RGui.exe** — простой интерактивный редактор для R. Аргументы командной строки для RGui.exe и RTerm одни и те же.

+ **RScript** — средство командной строки для выполнения скриптов R в пакетном режиме.

Чтобы найти эти средства, определите R библиотеки, в которой была установлена при установке SQL Server или автономный машинного обучения функции. Например по умолчанию при установке средств R находятся в этих папках:

+ Службы SQL Server 2016 R:`~\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64`
+ Изолированный сервер Microsoft R:`~\Program Files\Microsoft R\R_SERVER\bin\x64`
+ Машины SQL Server 2017 г. изучение служб:`~\Program Files\Microsoft SQL Server\MSSQL14.<instancename>\R_SERVICES\bin\x64`
+ Машинное обучение Server (изолированный):`~\Program Files\Microsoft\ML Server\R_SERVER\bin\x64`

Если вам нужна помощь с помощью средств R, просто откройте **RGui**, нажмите кнопку **справки**, а затем выберите один из вариантов.

## <a name="introducing-microsoft-r-client"></a>Знакомство с Microsoft R клиента

Клиент Microsoft R можно бесплатно загрузить, предоставляющая доступ к пакетам RevoScaleR для целей разработки. Установка клиента R, можно создать решения R, которые могут выполняться во всех контекстах поддерживаемых вычислений, включая анализа в базе данных SQL Server и распределенных вычислений в Hadoop, Spark или Linux с помощью сервера обучения Machine R.

Если вы уже установили другой среды разработки R, например RStudio, не забудьте изменить параметры среды для использования библиотек и исполняемых файлов, предоставляемые Microsoft R клиента. В результате можно использовать все возможности пакета RevoScaleR, несмотря на то, что производительности будет ограничен.

Дополнительные сведения см. в разделе [что такое клиент Microsoft R?](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)

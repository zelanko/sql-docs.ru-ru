---
title: Начало работы с SSMA для доступа к консоли (AccessToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 8585ec16-7e0a-483a-b250-adab9b9232a3
caps.latest.revision: 21
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 3a218ba28025f882d96cdfc122ceda01464419a3
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40394373"
---
# <a name="getting-started-with-ssma-for-access-console-accesstosql"></a>Начало работы с SSMA для доступа к консоли (AccessToSQL)
В этом разделе описывается, как запустить и приступить к работе с приложением доступа к консоли. Также в списке, в данном документе, соглашения используются в типичного окна выходных данных консоли SSMA.  
  
## <a name="launching-ssma-console"></a>Запуск консоли SSMA  
Следуйте инструкциям ниже, чтобы запустить приложение консоли SSMA:  
  
1.  Перейдите к **запустить** и пункты **все программы**.  
  
2.  Нажмите кнопку **SQL Server Migration Assistant для доступа к командной строке** ярлык.  
  
    Он отображает меню использования команд консоли SSMA и `(/? Help)`, чтобы помочь вам приступить к работе с консольного приложения.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Процедура использования консоли SSMA  
После в системе Windows успешно запускается консоль, работать с ним можно использовать следующие действия:  
  
1.  Настройка команд консоли SSMA через файлы скриптов. Дополнительные сведения об этом разделе, см. в разделе [Создание файлов сценария &#40;AccessToSQL&#41;](../../ssma/access/creating-script-files-accesstosql.md).  
  
2.  [Создание файлов переменных значений &#40;AccessToSQL&#41;](../../ssma/access/creating-variable-value-files-accesstosql.md)  
  
3.  [Создание файлов подключения к серверу &#40;AccessToSQL&#41;](../../ssma/access/creating-the-server-connection-files-accesstosql.md)  
  
4.  [Выполнение команд консоли SSMA &#40;AccessToSQL&#41; ](../../ssma/access/executing-the-ssma-console-accesstosql.md) в соответствии с потребностями проекта  
  
Дополнительные функции:  
  
1.  [Укажите пароль](managing-passwords-accesstosql.md) и экспортировать и импортировать его на других компьютерах окна  
  
2.  [Создание отчетов](generating-reports-accesstosql.md) для просмотра подробных xml вывод отчетов для оценки /conversion и миграции данных. Подробные сведения об ошибке отчеты также могут формироваться для команд обновления и синхронизации.  
  
## <a name="ssma-console-output-conventions"></a>Соглашения о выходных данных консоли SSMA  
При выполнении команды сценария SSMA и параметры, консольная программа отображает результаты и сообщения (сведения, ошибка, и т.д.) для пользователя на консоли или при необходимости перенаправляет выходные данные в XML-файл. Каждый тип сообщения в выходных данных принятое уникальный цвет. Например текстовое сообщение в белый цвет обозначает команд файла скрипта; этому параметру в зеленый цвет представляет запрос для ввода данных пользователем и т. д.  
  
![Вывод консоли SSMA](../../ssma/access/media/ssmaconsoleoutput.jpg "вывод консоли SSMA")  
  
Цвет Интерпретация выходных данных консоли в следующей таблице:  
  
|Color|Описание|  
|---------|---------------|  
|Красный|Неустранимая ошибка во время выполнения|  
|Серый|Отметка даты и времени, сообщение для пользователя|  
|White|Файл команд, тип сообщения|  
|Желтый|Предупреждение|  
|Зеленый|Строка для ввода данных пользователем|  
|Голубой|Начала, окончания и результат операции|  
  
## <a name="see-also"></a>См. также  
[Установка SQL Server Migration Assistant для Access](installing-sql-server-migration-assistant-for-access-accesstosql.md)  
  

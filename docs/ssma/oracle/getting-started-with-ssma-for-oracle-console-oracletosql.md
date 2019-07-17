---
title: Начало работы с SSMA для Oracle консоли (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Oracle Console, Console Output Conventions
- Oracle Console, Launching Console
ms.assetid: 667a5e4a-6848-4973-a72d-1287f64718ac
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 25cd6eb9c811548e6300c944c65c5530185d46e8
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68264501"
---
# <a name="getting-started-with-ssma--for-oracle-console-oracletosql"></a>Начало работы с консолью SSMA для Oracle (OracleToSQL)
В этом разделе описывается, как запустить и приступить к работе с Oracle консольного приложения. Также в списке, в данном документе, соглашения используются в типичного окна выходных данных консоли SSMA.  
  
## <a name="launching-ssma-console"></a>Запуск консоли SSMA  
Следуйте инструкциям ниже, чтобы запустить приложение консоли SSMA:  
  
1.  Перейдите к **запустить** и пункты **все программы**.  
  
2.  Нажмите кнопку  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant для Oracle командной строки** ярлык.  
  
    Он отображает меню использования команд консоли SSMA и `(/? Help)`, чтобы помочь вам приступить к работе с консольного приложения.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Процедура использования консоли SSMA  
После в системе Windows успешно запускается консоль, работать с ним можно использовать следующие действия:  
  
1.  Настройка команд консоли SSMA через файлы скриптов. Дополнительные сведения об этом разделе, см. в разделе [Создание файлов сценария &#40;OracleToSQL&#41; ](../../ssma/oracle/creating-script-files-oracletosql.md) .  
  
2.  [Создание файлов переменных значений &#40;OracleToSQL&#41;](../../ssma/oracle/creating-variable-value-files-oracletosql.md)  
  
3.  [Создание файлов подключения к серверу &#40;OracleToSQL&#41;](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md)  
  
4.  [Выполнение команд консоли SSMA &#40;OracleToSQL&#41; ](../../ssma/oracle/executing-the-ssma-console-oracletosql.md) в соответствии с потребностями проекта  
  
Дополнительные функции:  
  
1.  [Укажите пароль](managing-passwords-oracletosql.md) и экспортировать и импортировать его на других компьютерах окна  
  
2.  [Создание отчетов](generating-reports-oracletosql.md) для просмотра подробных xml вывод отчетов для оценки /conversion и миграции данных. Подробные сведения об ошибке отчеты также могут формироваться для команд обновления и синхронизации.  
  
## <a name="ssma-console-output-conventions"></a>Соглашения о выходных данных консоли SSMA  
При выполнении команды сценария SSMA и параметры, консольная программа отображает результаты и сообщения (сведения, ошибка, и т.д.) для пользователя на консоли или при необходимости перенаправляет выходные данные в XML-файл. Каждый тип сообщения в выходных данных принятое уникальный цвет. Например текстовое сообщение в белый цвет обозначает команд файла скрипта; этому параметру в зеленый цвет представляет запрос для ввода данных пользователем и т. д.  
  
![Вывод консоли ssma_oracle](../../ssma/db2/media/ssmaconsoleoutput_oracle.jpg "вывод консоли ssma_oracle")  
  
Цвет Интерпретация выходных данных консоли в следующей таблице:  
  
|Color|Описание|  
|---------|---------------|  
|Красный|Неустранимая ошибка во время выполнения|  
|Серый|Отметка даты и времени, сообщение для пользователя|  
|Белый|Файл команд, тип сообщения|  
|Желтый|Предупреждение|  
|Зеленый|Строка для ввода данных пользователем|  
|Голубой|Начала, окончания и результат операции|  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для Oracle](installing-ssma-for-oracle-oracletosql.md)  
  

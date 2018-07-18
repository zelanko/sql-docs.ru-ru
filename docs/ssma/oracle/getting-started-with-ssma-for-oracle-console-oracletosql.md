---
title: Начало работы с SSMA для Oracle консоли (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Oracle Console, Console Output Conventions
- Oracle Console, Launching Console
ms.assetid: 667a5e4a-6848-4973-a72d-1287f64718ac
caps.latest.revision: 31
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 86b8adc8841e06d91d164c2c35e2329511ac0e28
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2018
ms.locfileid: "38985756"
---
# <a name="getting-started-with-ssma--for-oracle-console-oracletosql"></a>Начало работы с SSMA для Oracle консоли (OracleToSQL)
В этом разделе описывается, как запустить и приступить к работе с Oracle консольного приложения. Также в списке, в данном документе, соглашения используются в типичного окна выходных данных консоли SSMA.  
  
## <a name="launching-ssma-console"></a>Запуск консоли SSMA  
Следуйте инструкциям ниже, чтобы запустить приложение консоли SSMA:  
  
1.  Перейдите к **запустить** и пункты **все программы**.  
  
2.  Нажмите кнопку  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant для Oracle командной строки** ярлык.  
  
    Он отображает меню использования команд консоли SSMA и `(/? Help)`, чтобы помочь вам приступить к работе с консольного приложения.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Процедура использования консоли SSMA  
После в системе Windows успешно запускается консоль, работать с ним можно использовать следующие действия:  
  
1.  Настройка команд консоли SSMA через файлы скриптов. Дополнительные сведения об этом разделе, см. в разделе [Создание файлов сценария &#40;OracleToSQL&#41; ](../../ssma/oracle/creating-script-files-oracletosql.md) .  
  
2.  [Создание файлов переменных значений &#40;OracleToSQL&#41;](../../ssma/oracle/creating-variable-value-files-oracletosql.md)  
  
3.  [Создание файлов подключения к серверу &#40;OracleToSQL&#41;](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md)  
  
4.  [Выполнение команд консоли SSMA &#40;OracleToSQL&#41; ](../../ssma/oracle/executing-the-ssma-console-oracletosql.md) в соответствии с потребностями проекта  
  
Дополнительные функции:  
  
1.  [Укажите пароль](http://msdn.microsoft.com/8c7d9f8e-06bb-476c-bbd2-15b61d5bba3c) и экспортировать и импортировать его на других компьютерах окна  
  
2.  [Создание отчетов](http://msdn.microsoft.com/ccad6262-01e1-447a-bd2b-c105154c80ce) для просмотра подробных xml вывод отчетов для оценки /conversion и миграции данных. Подробные сведения об ошибке отчеты также могут формироваться для команд обновления и синхронизации.  
  
## <a name="ssma-console-output-conventions"></a>Соглашения о выходных данных консоли SSMA  
При выполнении команды сценария SSMA и параметры, консольная программа отображает результаты и сообщения (сведения, ошибка, и т.д.) для пользователя на консоли или при необходимости перенаправляет выходные данные в XML-файл. Каждый тип сообщения в выходных данных принятое уникальный цвет. Например текстовое сообщение в белый цвет обозначает команд файла скрипта; этому параметру в зеленый цвет представляет запрос для ввода данных пользователем и т. д.  
  
![Вывод консоли ssma_oracle](../../ssma/db2/media/ssmaconsoleoutput_oracle.jpg "вывод консоли ssma_oracle")  
  
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
[Установка SSMA для Oracle](http://msdn.microsoft.com/9211013a-ab24-4c52-9b26-87994b35e502)  
  

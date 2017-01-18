# about_Sf_Filtering

## TOPIC

    XenDesktop - 高级数据集过滤 
    

## 简短说明

    介绍 XenDesktop cmdlet 的常用过滤选项。 
    

## 详细说明

    一些 cmdlet 操作对象是大量数据，为了减少通过网络发送所有数据的开销，许多 Get- cmdlet 支持在服务器端过滤结果。 
    
    在 PowerShell 中过滤结果的常规方法是通过管道将其传送到 Where-Object、Select-Object 和 Sort-Object，例如︰
    
      Get-<Noun> | Where { $_.Size = 'Small' } | Sort 'Date' | Select -First 10 
    
    但是，对于大多数 XenDesktop cmdlet，数据是远程存储，因此，通过网络检索大量数据，然后丢弃其中的大部分，这种方式速度慢且效率低。 而许多 Get- cmdlet 提供过滤参数，用于允许在服务器上处理结果，从而只返回所需结果。 
    
    可以使用从属性名称派生的参数通过大多数对象属性来过滤结果。 还可以对结果进行排序或将其限于指定的记录数︰
    
      Get-<Noun> -Size 'Small' -SortBy 'Date' -MaxRecordCount 10 
    
    可以使用与 PowerShell 表达式所用运算符非常相似的运算符的语法和集合来表达比较复杂的过滤条件。 
    
    支持过滤的 cmdlet 具有以下常用参数： 
    
    -MaxRecordCount < int > 
        指定要返回的最大结果数。 
        例如，若要只返回前 9 个结果，则使用︰
    
          Get-<Noun> -MaxRecordCount 9 
    
        如果不指定，则只返回前 250 条记录，如果有更多记录，将产生警告︰ 
    
        WARNING: Only first 250 records returned. Use -MaxRecordCount to retrieve more.（警告︰ 只返回前 250 条记录。可使用 -MaxRecordCount 检索更多结果。） 
    
        可以通过使用 -WarningAction 或为 -MaxRecordCount 指定值来禁止显示此警告。 
    
        若要检索所有记录，请为 -MaxRecordCount 指定较大数目。 
        由于值是一个整数，可以使用以下行︰
    
          Get-<Noun> -MaxRecordCount [int]::MaxValue 
    
    -ReturnTotalRecordCount [<SwitchParameter>] 
        如果指定此项，cmdlet 将输出包含可用记录数的错误记录。 此错误记录是附加信息，并不影响写入输出管道的对象。 例如： 
    
          Get-<Noun> -MaxRecordCount 9 -ReturnTotalRecordCount 
          .... 
    
          Get-<Noun> : Returned 9 of 10 items 
          At line:1 char:18 
          + Get-<Noun> <<<<  -MaxRecordCount 9 -ReturnTotalRecordCount 
          + CategoryInfo          : OperationStopped: (:) [Get-<Noun>], PartialDataException 
          + FullyQualifiedErrorId : PartialData,Citrix.<SDKName>.SDK.Get<Noun> 
    
        可以使用 TotalAvailableResultCount 属性访问计数：
    
          $count = $error[0].TotalAvailableResultCount 
    
    -Skip <int> 
        在返回结果之前跳过指定的记录数。 
        此外还降低由 -ReturnTotalRecordCount 返回的计数。 
    
    -SortBy <string> 
        按指定的属性列表对结果进行排序。 列表是一组由逗号、分号或空格分隔的属性名称。 
        （可选） 在每个名称加前缀 + 或 - 分别指示升序或降序排序。 如果没有前缀，则假设为升序排序。 
    
        排序发生在应用 -MaxRecordCount 和 -Skip 参数之前。 例如，若要先按名称排序，然后按计数排序（最大排第一），则使用：
    
          -SortBy 'Name,-Count' 
    
    默认情况下，按枚举属性排序时使用元素的数值。 可以通过使用元素或其数值的排序列表限定名称来指定不同的排序顺序，或指定 <null> 指示空值位置。 
        未提及的元素按其数值顺序置于末尾。 
        例如，先按两个不同的枚举排序，然后按对象 id 排序：
    
          -SortBy 'MyState(StateC,<null>,StateA,StateB),Another(0,3,2,1),Id' 
    
    -Filter <String> 
        此参数允许您指定高级过滤表达式，并支持使用 -and 和  -or 进行条件组合，以及使用大括号进行分组。 例如：
    
          Get-<Noun> -Filter 'Name -like "High*" -or (Priority -eq 1 -and Severity -ge 2)' 
    
        该语法非常接近于 PowerShell 语法，因此可以在大多数情况下使用脚本块。 这样更易读取，因为它减少了引用︰
    
          Get-<Noun> -Filter { Count -ne $null } 
    
    下文提供了完整的 -Filter 语法。 
    

## 示例

    按字符串过滤执行不区分大小写的通配符匹配。 
    单独的参数通过使用隐式 -and 运算符进行组合。 
    常规 PowerShell 引用规则适用，因此可以使用单引号或双引号，以及对许多字符串完全省略引号。 参数的顺序不会造成任何差异。 下列几项等效： 
    
      Get-<Noun> -Company Citrix -Product Xen* 
      Get-<Noun> -Company "citrix" -Product '[X]EN*' 
      Get-<Noun> -Product "Xen*" -Company "CITRIX" 
      Get-<Noun> -Filter { Company -eq 'Citrix' -and Product -like 'Xen*' } 
    
    请参阅 about_Quoting_Rules 和 about_Wildcards 了解有关 PowerShell 如何处理引号和通配符的详细信息。 
    
    若要避免通配符匹配或要包含引号字符，可以使用常规 PowerShell 转义机制（请参阅 about_Escape_Characters）转义通配符，或转为使用过滤表达式和 -eq 运算符︰ 
    
      Get-<Noun> -Company "Abc[*]" # 匹配 Abc* 
      Get-<Noun> -Company "Abc`*" # 匹配 Abc* 
      Get-<Noun> -Filter { Company -eq "Abc*" } # 匹配 Abc* 
      Get-<Noun> -Filter { Company -eq "A`"B`'C" } # 匹配 A"B'C 
    
    按数字、布尔值和时间范围进行的简单过滤执行直接的相等比较，虽然如果值可以为空值，还可以搜索空值。 下面是一些示例：
    
      Get-<Noun> -Uid 123 
      Get-<Noun> -Enabled $true 
      Get-<Noun> -Duration 1:30:40 
      Get-<Noun> -NullableProperty $null 
    
    可以通过 -Filter 使用高级过滤进行更多比较： 
    
      Get-<Noun> -Filter 'Capacity -ge 10gb' 
      Get-<Noun> -Filter 'Age -ge 20 -and Age -lt 40' 
      Get-<Noun> -Filter 'VolumeLevel -like "[123]"' 
      Get-<Noun> -Filter 'Enabled -ne $false' 
      Get-<Noun> -Filter 'NullableProperty -ne $null' 
    
    可以在不使用显式比较运算符的情况下检查布尔值，还可以使用 -not 对其进行组合：
    
      Get-<Noun> -Filter 'Enabled'      # 等同于 'Enabled -eq $true' 
      Get-<Noun> -Filter '-not Enabled' # 等同于 'Enabled -eq $false' 
    
    请参阅 about_Comparison_Operators 了解运算符的说明，但请注意，只支持一部分 PowerShell 运算符（-eq、-ne、-gt、-ge、-lt、-le、-like、-notlike、-in、-notin、-contains、-notcontains）。 
    
    可以使用类型化的值或枚举值的字符串名称指定枚举值︰ 
    
      Get-<Noun> -Shape [Shapes]::Square 
      Get-<Noun> -Shape Circle 
    
    使用过滤表达式时，可以使用简单变量或引用的字符串指定类型化的值。 它们也支持使用通配符的枚举︰
    
      $s = [Shapes]::Square 
      Get-<Noun> -Filter { Shape -eq $s -or Shape -eq "Circle" } 
      Get-<Noun> -Filter { Shape -like 'C*' } 
    
    由于其性质，浮点值、DateTime 值和时间范围值最适于相对比较，而不是仅仅相等比较。 
    DateTime 字符串是使用用户设备的区域设置和时区进行转换，但您可以使用 ISO8601 格式字符串 (YYYY-MM-DDThh:mm:ss.sTZD) 以避免多义性。 还可以使用标准 PowerShell 语法来创建这些值︰
    
      Get-<Noun> -Filter { StartTime -ge "2010-08-23T12:30:00.0Z" } 
      $d = [DateTime]"2010-08-23T12:30:00.0Z" 
      Get-<Noun> -Filter { StartTime -ge $d } 
      $d = (Get-Date).AddDays(-1) 
      Get-<Noun> -Filter { StartTime -ge $d } 
    
    相对时间很常见，使用过滤表达式时，还可以使用相对格式指定 DateTime 值︰
    
      Get-<Noun> -Filter { StartTime -ge '-2' }         # 2 天前 
      Get-<Noun> -Filter { StartTime -ge '-1:30' }      # 1.5 小时前
      Get-<Noun> -Filter { StartTime -ge '-0:0:30' }    # 30 秒前 
    

数组属性 按列表或数组属性过滤时，针对每个成员，简单参数执行不区分大小写的通配符匹配。 使用过滤表达式时，可以使用 -contains 和 -notcontains 运算符。 与 PowerShell 不同，这些针对字符串执行通配符匹配。 请注意，对于数组属性，命名约定是针对复数形式的返回属性，但用于搜索任何匹配的参数是单数。 以下几项等效（假设 Users 是一个数组属性）︰

      Get-<Noun> -User Fred* 
      Get-<Noun> -Filter { User -like "Fred*" } 
      Get-<Noun> -Filter { Users -contains "Fred*" } 
    
    还可以在 -Filter 中使用单数形式来使用其他运算符进行搜索：
    
      # 如果列表中的任何用户名为“Frederick”，则匹配
      Get-<Noun> -Filter { User -eq "Frederick" } 
      # 如果列表中的任何用户的姓名按字母顺序排在“F”后面，则匹配 
      Get-<Noun> -Filter { User -lt 'F' } 
    

复杂表达式 按多个值匹配时，可以使用通过 -or 连接的一系列比较，也可以使用 -in 和 -notin：

      Get-<Noun> -Filter { Shape -eq 'Circle' -or Shape -eq 'Square' } 
      $shapes = 'Circle','Square' 
      Get-<Noun> -Filter { Shape -in $shapes } 
      $sides = 1..4 
      Get-<Noun> -Filter { Sides -notin $sides } 
    
    可以使用大括号对复杂表达式分组，以及重写默认从左到右的 -and 和 -or 求值。 还可以使用 -not 反转任何子表达式的意义：
    
      Get-<Noun> -Filter { Size -gt 4 -or (Color -eq 'Blue' -and Shape -eq 'Circle') } 
      Get-<Noun> -Filter { Sides -lt 5 -and -not (Color -eq 'Blue' -and Shape -eq 'Circle') } 
    

分页 分页浏览数据的最简单方法是使用 -Skip 和 -MaxRecordCount 参数。因此，要按每页 10 条记录读取前三页数据，请使用︰

      Get-<Noun> -Skip 0  -MaxRecordCount 10 <other filtering criteria> 
      Get-<Noun> -Skip 10 -MaxRecordCount 10 <other filtering criteria> 
      Get-<Noun> -Skip 20 -MaxRecordCount 10 <other filtering criteria> 
    
    必须在每次调用中包括相同的过滤条件，并确保按一致方式对数据进行排序。 
    
    上述方法通常可以接受，但由于每次调用都执行独立的查询，因此数据更改可能会导致记录被跳过或出现两次。 为了改进这一点，可以使用这个方法：按一个唯一的 id 字段进行排序，然后从上一页最后一个唯一的 id 之后的唯一 id 开始搜索下一页。 例如：
    
      # 获取第一页 
      Get-<Noun> -MaxRecordCount 10 -SortBy SerialNumber 
    
      SerialNumber  ... 
      ------------  --- 
      A120004 
      A120007 
      ... 7 other records ... 
      A120900 
    
      # 获取下一页 
      Get-<Noun> -MaxRecordCount 10 -Filter { FirstName -gt 'A120900' } 
    
      SerialNumber  ... 
      ------------  --- 
      A120901 
      B220000 
      ... 
    

## 过滤器语法定义

    <Filter>        ::= <ScriptBlock> | <ComponentList> 
    
    <ScriptBlock>   ::= "{" <ComponentList> "}" 
    
    <ComponentList> ::= <Component> <AndOrOperator> <ComponentList> | 
                        <Component> 
    
    <Component>     ::= <NotOperator> <Factor> | 
                        <Factor> 
    
    <Factor>        ::= "(" <ComponentList> ")" | 
                        <PropertyName> <ComparisonOperator> <Value> | 
                        <PropertyName> 
    
    <AndOrOperator> ::= "-and" | "-or" 
    
    <NotOperator>   ::= "-not" | "!" 
    
    <ComparisonOperator> 
                    ::= "-eq" | "-ne" | "-le" | "-ge" | "-lt" | "-gt" | 
                        "-like" | "-notlike" | "-contains" | "-notcontains" | 
                        "-in" | "-notin" 
    
    <PropertyName>  ::= <simple name of property> 
    
    <Value>         ::= <string literal>  | <numeric literal> | 
                        <scalar variable> | <array variable>  | 
                        "$null" | "$true" | "$false" 
    
    数字文本支持十进制文本和十六进制文本，带可选系数后缀（kb、mb、gb、tb、pb）。 
    
    日期和时间可以指定为字符串文本。 当前区域性确定接受哪些格式。 为了避免任何多义性，应使用按 ISO8601 标准设置格式的字符串。 如果未指定，则使用当前时区。 
    
    此外还支持相对日期时间字符串文本，即，使用减号并后接时间范围。 例如，“-1:30”表示 1 小时 30 分钟前。
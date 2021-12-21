##### Zel

# Руководство Денчик слазит

[Если денчик не слазит, надо помочь](https://github.com/Zelgladis/Zel/blob/main/README.md#%D1%82%D1%80%D1%83-%D0%BA%D0%BE%D0%B4)

### Денчик слазит по спику
* денчик слазит 1
* денчик слазит 2
* Денчик слазит 3
  * Денчи все ещё слазит 3
* Не слазит 4

0. Цифра 1
0. Цифра 2
0. Цфи

> Цитируя денчика, денчик денчик денчик
> > А стасик стасик стасик

## Тру код
```Powershell
Add-Type -Assembly System.Windows.Forms 

function level_cleared {
    param (
        $level,
        $name = ''
    )
    foreach($item in $levels[$level..($levels.Count-1)])
        {
            foreach($item2 in $item)
            {
                if($item2.Name -ne $name){$item2.Visible = $false}
                else{$item2.Visible = $true}
            }
        }
    
}

function item_chaged 
{
    if($Combo_bisnes.Text -eq 'КИБ')
    {
        level_cleared 1 $label_perenap.Name
    } 
    elseif ($Combo_bisnes.Text -eq 'МСБ') 
    {
        level_cleared 1 $Combo_vopros.Name
    }
}

function item_chaged_vopros
{
    if($Combo_vopros.Text -eq 'Сообщение об ошибке')
    {
        level_cleared 2 $Combo_err.Name
    } 
    elseif ($Combo_vopros.Text -eq 'Настройка системы') 
    {
        level_cleared 2 $Combo_3.Name
    }
    else
    {
        level_cleared 2
    }
}

$window = New-object System.Windows.Forms.Form
$window.Text = 'Main Window'
$window.Height = 420
$window.Width = 600
$window.autosize = $true

#Labels
$label_1 = New-Object System.Windows.Forms.Label
$label_1.Text = 'Hello World!'
$label_1.Font = New-Object System.Drawing.Font("Microsoft Sans Serif", 12, [System.Drawing.FontStyle]::Bold)
$label_1.AutoSize = $true
$label_1.Location = New-Object System.Drawing.Point(10, 10)
$window.controls.add($label_1)

#Combo1
$Combo_bisnes = New-Object System.Windows.Forms.ComboBox
$Combo_bisnes.Name = 'C_bisnes'
$Combo_bisnes.Font = New-Object System.Drawing.Font("Microsoft Sans Serif", 12, [System.Drawing.FontStyle]::Bold)
$Combo_bisnes.AutoSize = $true
$Combo_bisnes.Location = New-Object System.Drawing.Point(10, 40)
$Combo_bisnes.DataSource = @('','КИБ', 'МСБ', 'Другое')
$Combo_bisnes.add_TextChanged({ item_chaged })
$window.controls.add($Combo_bisnes)

#Combo2
$Combo_vopros = New-Object System.Windows.Forms.ComboBox
$Combo_vopros.Name = 'C_vopros'
$Combo_vopros.Font = New-Object System.Drawing.Font("Microsoft Sans Serif", 12, [System.Drawing.FontStyle]::Bold)
$Combo_vopros.AutoSize = $true
$Combo_vopros.Size = New-Object System.Drawing.Size(300, 20)
$Combo_vopros.Location = New-Object System.Drawing.Point(10, 80)
$Combo_vopros.DataSource = @("", 'Сообщение об ошибке', "настройка системы", "что-то ещё")
$Combo_vopros.add_TextChanged({ item_chaged_vopros })
$Combo_vopros.Visible = $false
$window.controls.add($Combo_vopros)

#Labels
$label_perenap = New-Object System.Windows.Forms.Label
$label_perenap.Name = 'L_perenap'
$label_perenap.Text = 'Воспользуйтес сервисом КИБ'
$label_perenap.Font = New-Object System.Drawing.Font("Microsoft Sans Serif", 14, [System.Drawing.FontStyle]::Bold)
$label_perenap.AutoSize = $true
$label_perenap.Location = New-Object System.Drawing.Point(10, 80)
$label_perenap.Visible =  $false
$window.controls.add($label_perenap)

#$Combo_2 | Get-Member -MemberType Event

#level 3
#Combo3
$Combo_err = New-Object System.Windows.Forms.ComboBox
$combo_err.Name = 'C_err'
$Combo_err.Font = New-Object System.Drawing.Font("Microsoft Sans Serif", 12, [System.Drawing.FontStyle]::Bold)
$Combo_err.AutoSize = $true
$Combo_err.Size = New-Object System.Drawing.Size(300, 20)
$Combo_err.Location = New-Object System.Drawing.Point(10, 120)
$Combo_err.DataSource = @('', "Доступ к карточке", "Доступ к сделке", "Отправка письма" ,"нет в списке")
$Combo_err.Visible = $false
$window.controls.add($Combo_err)

#Combo3
$Combo_3 = New-Object System.Windows.Forms.ComboBox
$combo_3.Name = 'Combo_3'
$Combo_3.Font = New-Object System.Drawing.Font("Microsoft Sans Serif", 12, [System.Drawing.FontStyle]::Bold)
$Combo_3.AutoSize = $true
$Combo_3.Location = New-Object System.Drawing.Point(10, 120)
$Combo_3.DataSource = @(111,222,333,444,555)
$Combo_3.Visible = $false
$window.controls.add($Combo_3)

#grooping
$level_1 = @($Combo_bisnes)
$level_2 = @($Combo_vopros, $label_perenap)
$level_3 = @($Combo_err, $Combo_3)
$levels = [System.Collections.ArrayList]@($level_1, $level_2, $level_3)

$window.ShowDialog()

```

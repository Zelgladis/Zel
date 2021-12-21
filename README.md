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

$window = New-object System.Windows.Forms.Form
$window.Text = 'Самая полезная программа'
$window.Height = 500
$window.Width = 500
$window.autosize = $true

$vihod_1 = New-Object System.Windows.Forms.Button
$vihod_1.Text = 'Выход'
$vihod_1.Font = New-Object System.Drawing.Font("Microsoft Sans Serif", 11)
$vihod_1.AutoSize = $true
$vihod_1.Location = New-Object System.Drawing.Point(10, 420)
$vihod_1.add_click({ $window.Close() })
$window.controls.add($vihod_1)

$vihod_2 = New-Object System.Windows.Forms.Button
$vihod_2.Text = 'Тоже выход выход'
$vihod_2.Font = New-Object System.Drawing.Font("Microsoft Sans Serif", 11)
$vihod_2.AutoSize = $true
$vihod_2.Location = New-Object System.Drawing.Point(325, 420)
$vihod_2.add_click({ $window.Close() })
$window.controls.add($vihod_2)


Add-Type –memberDefinition @'
[DllImport("user32.dll")]
public static extern bool ShowWindowAsync(IntPtr hWnd, int nCmdShow);
'@ -name Win32ShowWindowAsync -namespace Win32Functions
#minimize window
[Win32Functions.Win32ShowWindowAsync]::ShowWindowAsync((Get-Process –id $pid).MainWindowHandle, 2)
$window.ShowDialog()

```

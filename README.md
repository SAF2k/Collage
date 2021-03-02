5.Design a VB interface containing 

a. A picture box whose picture should be changed every 5 second (use 5 pictures).

 b. Textboxes to display date & time and day greeting based on time. 

Time has to be changed every second automatically.

 c. Use scrollbars to change font size and background color (RGB) of the textbox that shows greeting. [Use timer, scrollbars]

3. Design a form to accept number of books to be ordered to a shop in a textbox. By clicking a button ‘Continue’, if accepted number is > 0, then place required number of textboxes on the form to accept the details Title, Author and Copies, during run time to accept details of specified number of books. By clicking a button ‘Next’ on this form, enabling progression bar, send the details to another form to show the summary of the books ordered.

Public Class orderbook

    Dim m_orderbook As SHOWORDER

    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click

        disable()

        If IsNumeric(txtno.Text) Then

            If txtno.Text <= 6 Then

                For i As Integer = 1 To txtno.Text

                    DirectCast(Me.Controls("txtt" + CStr(i)), TextBox).Visible = True

                    DirectCast(Me.Controls("txta" + CStr(i)), TextBox).Visible = True

                    DirectCast(Me.Controls("txtc" + CStr(i)), TextBox).Visible = True

                Next

            End If

        End If

    End Sub

    Private Sub orderbook_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load

        disable()

    End Sub

    Public Sub disable()

        For i As Integer = 1 To 6

            DirectCast(Me.Controls("txtt" + CStr(i)), TextBox).Visible = False

            DirectCast(Me.Controls("txta" + CStr(i)), TextBox).Visible = False

            DirectCast(Me.Controls("txtc" + CStr(i)), TextBox).Visible = False

        Next

    End Sub

    Private Sub Button2_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button2.Click

        Dim txtmsg As New TextBox

        txtmsg.Text = "YOUR ORDER FOR " & Me.txtno.Text & "BOOKS RECEIVED"

        txtmsg.AppendText(Environment.NewLine)

        For i As Integer = 1 To txtno.Text

            txtmsg.AppendText(DirectCast(Me.Controls("txtt" + CStr(i)), TextBox).Text + "-" + DirectCast(Me.Controls("txta" + CStr(i)), TextBox).Text + "-" + DirectCast(Me.Controls("txtc" + CStr(i)), TextBox).Text)

            txtmsg.AppendText(Environment.NewLine)

        Next

        m_orderbook = New SHOWORDER(txtmsg.Text)

        m_orderbook.Show()

    End Sub

End Class

Public Class showorder

    Dim m_msg As String

    Public Sub New(ByVal msg As String)

        InitializeComponent()

        m_msg = msg

    End Sub

    Private Sub showorder_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load

        txtmsg.Text = m_msg

       

    End Sub

End Class

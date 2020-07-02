Pikwy - Online Solution to create Screenshot <br>
<a style="color:white" href="https://pikwy.com/api.html">Documentation</a><br>

VB.NET examples:<br>

    Imports System
    Imports System.net
    Public Module PikwyClient
      Public Sub Main()
            Dim token As String
            Dim ApiUrl As String
            Dim UrlOpt As Url_Options	
            token = "YOUR_API_TOKEN"

            UrlOpt.url = "https://www.wikipedia.org/"
            UrlOpt.width = 1280
            UrlOpt.height = 1024
            UrlOpt.response_type = "image"

            REM Parameters.
            ApiUrl = "https://api.pikwy.com/?token=" & token
            If token <> "" Then
                ApiUrl = ApiUrl & "&url=" & UrlOpt.url
                ApiUrl = ApiUrl & "&width=" & UrlOpt.width
                ApiUrl = ApiUrl & "&height=" & UrlOpt.height
                ApiUrl = ApiUrl & "&response_type=" & UrlOpt.response_type
            End If

            REM Save screenshot as an image.
            Dim Client As New WebClient
            Dim output As String = "\output.png"
        Console.WriteLine(ApiUrl)
            Client.DownloadFile(ApiUrl, output)		
        Console.WriteLine("The file was saved!")
      End Sub
    End Module

    Module PikwyOptions
        Public Structure Url_Options
            Public url As String
            Public width As Integer
            Public height As Integer
            Public response_type As String
        End Structure
    End Module

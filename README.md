# google-translation
jquery google ajax translation English to Spanish


            $('#translate-box').bind('input propertychange', function() {

                var qq = $("#translate-box").val();
                
                $.ajax({  
                    url: 'https://www.googleapis.com/language/translate/v2',  
                    dataType: 'jsonp',
                    data: { key: 'MY-KEY',
                            q: qq,  
                            source: 'en',
                            target: 'es'},  
                    success: function(result) {
                        $("#translation-result").empty();
                        try {
                            $.each(result.data.translations, function( index, value ) {
                               $("#translation-result").text(value.translatedText);
                            });
                           
                        }
                        catch(err) {
                            $("#translation-result").text(result.error.message);
                        }
                        
                    },  
                    error: function(XMLHttpRequest, errorMsg, errorThrown) {
                        $("#translation-result").empty();
                            $("#translation-result").text("Something went wrong");
                    }  
                });
            });

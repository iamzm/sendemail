# sendemail
# Sending via Gmail, Yahoo, Outlook
# Just pass params
# Call the funcations name by 

For sending email via Gmail
// Code


public static bool SendEmailViaGmail(string emailFrom, string password, string emailTo, string subject, string body)
        {
            try
            {
                string smtpAddress = "ssmtp.gmail.com";
                int portNumber = 587;
                bool enableSSL = true;
                using (MailMessage mail = new MailMessage())
                {
                    mail.From = new MailAddress(emailFrom);
                    mail.To.Add(emailTo);
                    mail.Subject = subject;
                    mail.Body = body;
                    mail.IsBodyHtml = true;
                    //mail.Attachments.Add(new Attachment("C:\\SomeFile.txt"));
                    //mail.Attachments.Add(new Attachment("C:\\SomeZip.zip"));
                    using (SmtpClient smtp = new SmtpClient(smtpAddress, portNumber))
                    {
                        smtp.Credentials = new NetworkCredential(emailFrom, password);
                        smtp.EnableSsl = enableSSL;
                        smtp.Send(mail);
                    }
                }
                return true;
            }
            catch (Exception)
            {
                return false;
            }
        }
        
        and Simimlary for Yahoo 
        SendEmailViaYahoo (.......)
        
        and also for Outlook /Hotmail
        
        SendEmailViaOutlook(string emailFrom, string password, string emailTo, string subject, string body)
        
        

# Blog__3

AWS services and how cen we access and use them uisng Python programming language?

As we all know AWS had many services, and here I am talking about the services that can be used practically by individuals. example for that is the translation service, face Rekognition, object detection, Transcription, and many other services.

Some of those services could be used using the console and  so if you just have one work to do, you can just access them through the console and do the work. but in most cases people would need to use them on multiple objects or files, it could go up to thousands and maybe millions and it is impossible to do that using the console only because would take days and maybe years.

At one point there has to be away where you can use programming to just loop through  your files and send the works to AWS. For that reason AWS built their very nice library, BOTO3, that can be used to access the vast majority of their services usnig programming languages and here I will be talking from PYthon prespectives only because that is where I master :)

In my opinion, the easiest way to explain anything and make it easy to understand is by using examples and so here I will use example of AWS transcription service and how we can connect to it. After that I will just tell you where you can go and find the main resource for anything that you could need in usnig boto3 library. 

First you need to donwload the library(pip3 install boto3) or if you are using Lambda, it is already pre-installed on their servers.

then just import it. (import boto3)

then it comes to assign the transcription service to a variable

        transcribe = boto3.client("transcribe")
        
Now you are offically have the connection ready to the service, all what you need is choose the api you want to use in the service. Here I will be using start_transcription_job api.

         transcribe.start_transcription_job(TranscriptionJobName = job_name,
                                        Media = {"MediaFileUri": s3_uri},   ##s3_URI IS WHERE LINK OF THE S3 OBJECT THAT YOU WANT TO DO THE WORK ON
                                        MediaFormat = MP4,
                                        LanguageCode = en,
                                        OutputBucketName="*NAME OF BUCKET WHERE THE OUTPUT WILL BE SENT TO*",
                                        #OutputEncryptionKMSKeyId='string',
                                        Settings={
                                            'ShowSpeakerLabels': True,
                                            'MaxSpeakerLabels': 10,
                                            'ShowAlternatives': True,
                                            'MaxAlternatives': 10
                                        })
        
        
CONGRATULATIONS!!! you already have sent the job to be processed by AWS Transcription service.

Finally, to check all other services and how to use all of the different APIs in them, you can look at the AWS documentation for Boto3 library. it has all of the services listed and all apis in them. Here is the link for that:

https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/transcribe.html

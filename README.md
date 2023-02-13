# Sign-action-signtool.exe
This action has been developed to be used in [Ginger](https://github.com/Ginger-Automation/Ginger) CI/CD, Ginger is a open source automation framework build by **Amdocs**.

Check it out - [https://ginger.amdocs.com/](https://ginger.amdocs.com/)

## Code sign a file
This action signs files using windows signtool.exe with a code signing certificate(it takes password).

This action works only on Windows and that means the workflow should run on windows-latest.

## Inputs

| Input  | Required  | Description |
| :------------: |:---------------:| :----------|
| filepath            | True        |  The path that contains the libraries to sign |
| certificate        | True        |    The PEM certificate file |
| cert-password | True        |   Certificate Password |
| timeStampUrl | Optional |  Optional Url of the timestamp server(Default is 'http://timestamp.digicert.com')  |


#### Creating certificate PEM file

To get the PEM certificate file of the PFX file, run the following in powershell:

 ``` openssl pkcs12 -in filename.pfx -out cert.pem -nodes ```
* file name should be change to pfx file name

Once you run the command, you will recive cert.pem, open it and copy the content and save it into project secrets.

You may find the secrets page by navigating to **Settings > Secrets > Actions** on your current repo.


## Example usage:
```
runs-on: windows-latest
	steps:
		-   uses: nadeemjazmawe/Sign-action-signtool.exe@v0.1
			with: 
				  filepath: 'D:\a\Installers\App.exe'   
				  certificate: ${{ secrets.PEM_FILE }}
				  cert-password: ${{ secrets.CERT_PASSWORD }}
				  timeStampUrl: ${{ secrets.TIME_STAMP_URL }}
```




***Enjoy Using it***

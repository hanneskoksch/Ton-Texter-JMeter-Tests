# Ton-Texter JMeter Tests

This repository includes JMeter tests for automated testing of the [Ton-Texter application](https://github.com/hanneskoksch/ton-texter). The following tests are included:



## `Ton-Texter_load_test.jmx`

This test logs in to Ton-Texter as a test user, automatically uploads 37 files in sequence, and triggers their transcription.
It is a load test to test against the Ton-Texter performance goals:

> Transcribe audio files with a total length of 10 hours within 10 minutes. 
> Use files of different lengths (30 seconds - 30 minutes).

This test has to be run manually. It uses the `audio_files.csv` to read the audio files. The audio/test files (except one, see test case below) are not included in the repository and must be manually added to `/testfiles`.



## `Ton-Texter_quick_test.jmx`

This test logs in to Ton-Texter as a test user, uploads a file (located in `testfiles`), triggers its transcription and waits for the transcription to finish. After the upload, the test waits a maximum of 5 minutes and periodically checks the transcription status to see if the transcription was successful so that the test can be terminated earlier. If the maximum time is reached without success, an error is logged that can be picked up by GitHub actions, for example. 

This test can be integrated in several places to automatically test and confirm the functionality of the entire Ton-Texter workflow, e.g. after a new build. 

## Related Repositories

| Service                                                      | Description                                                  | Scope                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ | --------------------- |
| [Ton-Texter](https://github.com/hanneskoksch/ton-texter) | The Next.js application.          | Next.js |
| [Cloud-Transcription-Service](https://github.com/ns144/Cloud-Transcription-Service) | AWS cloud infrastructure via Terraform and Lambdas.          | Transcription Service |
| [Transcription-Application](https://github.com/ns144/Transcription-Application) | The python application that does the transcription and the speaker diarization. | Transcription Service |
| [Cloud-Transcription-Machine](https://github.com/ns144/Cloud-Transcription-Machine) | The EC2 machine setup.                                       | Transcription Service |
| [Ton-Texter-JMeter-Tests](https://github.com/hanneskoksch/Ton-Texter-JMeter-Tests) | JMeter load and quick tests of the Ton-Texter application.   | End-to-end            |

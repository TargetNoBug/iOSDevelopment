``` Objective-C
-(void)renameFilesAtDirectory:(NSString *) directory
                   fileFormat:(NSString *) fileFormat
                       prefix:(NSString *) prefix
                       suffix:(NSString *) suffix
{
    NSError *error;
    NSArray *oldFileNames=[[NSFileManager defaultManager] contentsOfDirectoryAtPath:directory error:&error];
    NSLog(@"oldFileNames=%@",oldFileNames);
    for (NSString *oldFileName in oldFileNames) {
        if ([oldFileName hasSuffix:fileFormat]) {
            NSString *newFileName=[NSString stringWithFormat:@"%@%@%@",prefix,oldFileName,suffix];
            NSString *oldFilePath=[NSString stringWithFormat:@"%@/%@",directory,oldFileName];
            NSString *newFilePath=[NSString stringWithFormat:@"%@/new/%@",directory,[newFileName substringFromIndex:3]];
            
            [[NSFileManager defaultManager] moveItemAtPath:oldFilePath
                                                    toPath:newFilePath
                                                     error:&error];
            NSLog(@"error=%@",error);
        }
    }
}
```

``` Objective-C
```

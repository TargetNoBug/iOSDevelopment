get lost:

写法1:
``` C
@interface XXXManager : XXX

+(void)updateDeliveryAddressWithDeliveryAddressId:(int) deliveryAddressId
                               communityAddressId:(int) communityAddressId
                                 buildingNumberId:(int) buildingNumberId
                                   buildingUnitId:(int) buildingUnitId
                                 floorInformation:(NSString *) floorInformation
                                        consignee:(NSString *) consignee
                                        telephone:(NSString *) telephone
                                       completion:(XXNetworkingCodeMsgHandler) completion;
+(void)reloadCommunityAddressWithRegionCityId:(NSString *) regionCityId
                               correctHandler:(void(^)(NSArray <XXAddressCommunityItem *>* items)) correctHandler
                                 errorHandler:(XXNetworkingCodeMsgHandler) errorHandler;  
@end                                 
```

``` C

```                                       
                                     

写法2:
在view controller的某个请求方法里:
``` C
-(void)requestForData
{
  NSDictionary *dic=[XXXxxxHttpParams xxDicWithXxx:xx];
    [XxxxxxHttpReqRespHandler postURLString:XXURLForAPI(xxURL)
                                  paramsDic:dic
                             correctHandler:^(XxxHttpResponse *response) {
 
                             } errorHandler:^(int code, NSString *message) {
                                 [self xx_showTip:message];
                             }];
}
```
    

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
@implementation XXXManager
+(void)updateDeliveryAddressWithDeliveryAddressId:(int) deliveryAddressId
                               communityAddressId:(int) communityAddressId
                                 buildingNumberId:(int) buildingNumberId
                                   buildingUnitId:(int) buildingUnitId
                                 floorInformation:(NSString *) floorInformation
                                        consignee:(NSString *) consignee
                                        telephone:(NSString *) telephone
                                       completion:(IGNetworkingCodeMsgHandler) completion
{
    NSDictionary *dic=@{@"deliveryAddressId":@(deliveryAddressId),
                        @"sessionId":kUserinfoManager.sessionId,
                        @"accountId":@(kUserinfoManager.accountId),
                        @"communityAddressId":@(communityAddressId),
                        @"buildingNumberId":@(buildingNumberId),
                        @"buildingUnitId":@(buildingUnitId),
                        @"floorInformation":floorInformation?floorInformation:@"",
                        @"consignee":consignee,
                        @"telephone":telephone};
    [XxxxxxHttpReqRespHandler postURLString:XXURLForAPI(@"address/updateDeliveryAddress")
                                  paramsDic:dic
                            responseHandler:^(XxxxxxHttpResponse *response) {
                                completion(response.code,response.message);
                            }];
}

+(void)reloadCommunityAddressWithRegionCityId:(NSString *) regionCityId
                               correctHandler:(void(^)(NSArray <IGAddressCommunityItem *>* items)) correctHandler
                                 errorHandler:(IGNetworkingCodeMsgHandler) errorHandler
{
    NSDictionary *dic=@{@"sessionId":kUserinfoManager.sessionId,
                        @"accountId":@(kUserinfoManager.accountId),
                        @"regionCityId":regionCityId};
    [XxxxxxHttpReqRespHandler postURLString:IGURLForAPI(@"address/reloadCommunityAddress")
                                  paramsDic:dic
                            responseHandler:^(XxxxxxHttpResponse *response) {
                                if (response.code==kIGCorrectResponseCode) {
                                    NSArray <XXAddressCommunityItem *>*items=[NSArray yy_modelArrayWithClass:[XXAddressCommunityItem class] json:response.dataDic[@"someKey"]];
                                    correctHandler(items);
                                }else{
                                    errorHandler(response.code,response.message);
                                }
                            }];
}
@end  
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
    

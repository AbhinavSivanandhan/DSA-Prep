#Maximum of Minimum distances - 

Brute force:
given baskets and balls, iterate through minimum distances. at minimum distance =1 , place all balls and see is possible. increment minimal distance, md =2. then try again. stop when no longer possible to place all balls at that md and then return md. if  pos =[1,4,8,9] and md=1, balls=3, place b1=1, then place b2=incremented position which satisfied md>=1 which is 4, then place b3 at 8. so by trial and error, answer is possible at 1,2,3 but not 4 and beyond. As we increase, we cannot, but as we decrease md, w can place the balls. for such problems when searching space,(i.e, a monotonic function) use binary search



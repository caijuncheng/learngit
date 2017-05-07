diff --git a/apps/newipc/source/bll_presenter/preview.cpp b/apps/newipc/source/bll_presenter/preview.cpp
index 704b016..54a4aba 100755
--- a/apps/newipc/source/bll_presenter/preview.cpp
+++ b/apps/newipc/source/bll_presenter/preview.cpp
@@ -359,10 +359,10 @@ int PreviewPresenter::NormalInit()
     // 添加camera id和recorder type id到id group
     GroupID src0_id = {CAM_NORMAL_0, ISE_UNUSED};
-    RecDescInfo grp0_rec0 = {src0_id, REC_720P30FPS, REC_NORMAL, STREAM_SENDER_NONE};
-    grp0_rec_info_set.push_back(grp0_rec0);
+    // RecDescInfo grp0_rec0 = {src0_id, REC_720P30FPS, REC_NORMAL, STREAM_SENDER_NONE};
+    // grp0_rec_info_set.push_back(grp0_rec0);
 
-    RecDescInfo grp0_rec1 = {src0_id, REC_S_720P30FPS, REC_STREAM, STREAM_SENDER_RTSP};
+    RecDescInfo grp0_rec1 = {src0_id, REC_S_1080P30FPS, REC_STREAM, STREAM_SENDER_RTSP};
     grp0_rec_info_set.push_back(grp0_rec1);
 
     RecDescInfo grp0_rec2 = {src0_id, REC_S_VGA30FPS, REC_STREAM, (StreamSenderType)(STREAM_SENDER_RTSP|STREAM_SENDER_TUTK)};
diff --git a/apps/newipc/source/device_model/media/camera/camera_factory.cpp b/apps/newipc/source/device_model/media/camera/camera_factory.cpp
index 0dc964d..0a0fe49 100755
--- a/apps/newipc/source/device_model/media/camera/camera_factory.cpp
+++ b/apps/newipc/source/device_model/media/camera/camera_factory.cpp
@@ -36,10 +36,10 @@ Camera *CameraFactory::CreateCamera(CameraID cam_id)
             camera = this->CreateFisheyeCamera(CAM_B);
             break;
         case CAM_NORMAL_0:
-            camera = this->CreateNormalCamera(CAM_A);
+            camera = this->CreateNormalCamera(CAM_B);
             break;
         case CAM_NORMAL_1:
-            camera = this->CreateNormalCamera(CAM_B);
+            camera = this->CreateNormalCamera(CAM_A);
             break;
         case CAM_UVC_0:
             camera = this->CreateUVCCamera(CAM_A);
@@ -167,7 +167,7 @@ Camera *CameraFactory::CreateNormalCamera(PhysicalCameraID phy_cam_id)
     CameraInitParam param;
 
     // TODO: 录像分辨率大于camera分辨率的处理
-    SIZE_S size = {1280, 720};
+    SIZE_S size = {1920, 1080};
     param.cam_param_.setVideoSize(size);
 
     if (phy_cam_id == CAM_B) {

     this is change param.

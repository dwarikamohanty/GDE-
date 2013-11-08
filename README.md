/*
* Copyright (c) 2013 Expedia, Inc. All rights reserved.
*/
package com.expedia.rajni;

import javax.inject.Inject;

import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;
import org.springframework.stereotype.Component;

import com.expedia.rajni.service.BookingService;
import com.expedia.rajni.service.DealService;

/**
* 
* @author Dwarika Mohanty(dmohanty@expedia.com)
*/
@Component
public class Rajni {
@Inject private BookingService bookingService;
@Inject private DealService dealService;

@SuppressWarnings("resource")
public static void main(String[] args) throws Exception {
ApplicationContext appContext = new AnnotationConfigApplicationContext(RajniConfig.class);
Rajni rajni = appContext.getBean(Rajni.class);
rajni.checkEverything();
}

public void checkEverything() {
bookingService.checkBookings();
dealService.checkDeals();
}
}

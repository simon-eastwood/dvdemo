import React, { ReactElement, useEffect } from 'react';
import { BrowserRouter as Router, Routes, Route } from 'react-router-dom';
import './App.css';
import MainLoginPage from './pages/MainLoginPage';
import { GlobalStyle } from '../styles/global-styles';
import i18n from '../i18n';
import { environment } from '../utils/constants';

import { initReactI18next } from 'react-i18next';
import UploadPage from './pages/UploadPage';
import EpoHeader from './components/EpoHeader';
import SubmissionConfirmationPage from './pages/SubmissionConfirmationPage';
import { useAppSelector } from '../hooks/useTypedSelector';
import { Card, CardContent } from '@mui/material';
import SubmissionDetailsPage from './pages/SubmissionDetailsPage';
import SubmissionsListPage from './pages/SubmissionsListPage';
import EpoFooter from './components/EpoFooter/EpoFooter';

const App = (): ReactElement => {
    const { selectedLanguage } = useAppSelector((state) => state.app);
    i18n.use(initReactI18next).init({ lng: selectedLanguage.toLowerCase() });
    
    let baseUri = '';
    if (window.location.href.indexOf('internal.epo.org')) {
        baseUri = `${environment.namespace}/${environment.baseUri}`;
    }

    return (
        <Router basename={baseUri}>
            <GlobalStyle />
            <Card sx={{ width: '60%', height: 'auto', margin: '3rem auto', overflow: 'inherit' }}>
                <CardContent sx={{ padding: '0!important' }}>
                    <div className="App mb-12">
                        <EpoHeader />
                        <div style={{ paddingTop: '150px', width: '85%', margin: 'auto' }} id="content">
                            <Routes>
                                <Route index element={<MainLoginPage />} />
                                <Route path="/upload-page/*" element={<UploadPage />} />
                                <Route path="/upload-confirmation" element={<SubmissionConfirmationPage />} />
                                <Route path="/submissions/details" element={<SubmissionDetailsPage />} />
                                <Route path="/submissions" element={<SubmissionsListPage />} />
                            </Routes>
                        </div>
                    </div>
                    <EpoFooter showOnlyLowerSection={true}></EpoFooter>
                </CardContent>
            </Card>
        </Router>
    );
};

export default App;

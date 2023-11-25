# usefull_functions

//====shared layout effect =====
//----- like when click on image it open in model with animate ---

https://blog.sethcorker.com/framer-motion-shared-layout-gallery-animation/










example code in reactjs :-

import Typography from '@mui/material/Typography';
import Button from '@mui/material/Button';
import * as React from 'react';
import Modal from '@mui/material/Modal';
import { motion, AnimateSharedLayout, AnimatePresence } from "framer-motion";
const style = {
  position: 'absolute',
  top: '50%',
  left: '50%',
  transform: 'translate(-50%, -50%)',
  width: 400,
  bgcolor: 'background.paper',
  border: '2px solid #000',
  boxShadow: 24,
  p: 4,
};

// --custom theame hook in mui--
import { Box, Container, Grid, Paper, ThemeProvider, createTheme } from '@mui/material'
import { useState } from 'react';

const theameCreate = createTheme({
  palette: {
    primary: {
      main: "#73A9AD",
      dark: "#73A9AD",
      light: "#f6f6f6",
      contrastText: "#f6f6f6"
    },
    secondary: {
      main: "#1D267D",
      dark: "#0C134F"
    },
  },
})


function App() {

  const [layoutIdSet, setlayoutIdSet] = useState(null)
  const [open, setOpen] = React.useState(false);
  const handleOpen = () => setOpen(true);
  const handleClose = () => { setOpen(false), setlayoutIdSet(null) };
  return (
    <>
      <h1>learn mui</h1>


      <>
        {/* --grid-- */}
        <Container sx={{ background: '' }} maxWidth="xl">

          <Grid container spacing={5} columns={{ xs: 2 }}>


            <AnimatePresence>

              <Grid item>
                <Box sx={{ border: "1px solid gray", p: 2 }}>
                  <img src="https://picsum.photos/200/300" alt="" />
                  <motion.div key={1} layoutId={`product-${1}`} className={`bookEffect ${layoutIdSet === 1 && "active"}`} onClick={() => { setOpen(true), setlayoutIdSet(1) }}>
                    <div className="layer layerOne">
                      <span>M</span>
                    </div>
                    <div className="layer backLayer"></div>
                    <div className="coverLine"></div>
                  </motion.div>
                </Box>
              </Grid>
              <Grid item>
                <Box sx={{ border: "1px solid gray", p: 2 }}>
                  <img src="https://picsum.photos/200/300" alt="" />
                  <motion.div key={2} layoutId={`product-${2}`} className={`bookEffect ${layoutIdSet === 1 && "active"}`} onClick={() => { setOpen(true), setlayoutIdSet(2) }}>
                    <div className="layer layerOne">
                      <span>M</span>
                    </div>
                    <div className="layer backLayer"></div>
                    <div className="coverLine"></div>
                  </motion.div>
                </Box>
              </Grid>
              <Grid item>
                <Box sx={{ border: "1px solid gray", p: 2 }}>
                  <img src="https://picsum.photos/200/300" alt="" />
                  <motion.div key={3} layoutId={`product-${3}`} className={`bookEffect ${layoutIdSet === 1 && "active"}`} onClick={() => { setOpen(true), setlayoutIdSet(3) }}>
                    <div className="layer layerOne">
                      <span>M</span>
                    </div>
                    <div className="layer backLayer"></div>
                    <div className="coverLine"></div>
                  </motion.div>
                </Box>
              </Grid>
              <Grid item>
                <Box sx={{ border: "1px solid gray", p: 2 }}>
                  <img src="https://picsum.photos/200/300" alt="" />
                  <motion.div key={4} layoutId={`product-${4}`} className={`bookEffect ${layoutIdSet === 1 && "active"}`} onClick={() => { setOpen(true), setlayoutIdSet(4) }}>
                    <div className="layer layerOne">
                      <span>M</span>
                    </div>
                    <div className="layer backLayer"></div>
                    <div className="coverLine"></div>
                  </motion.div>
                </Box>
              </Grid>
              <Grid item>
                <Box sx={{ border: "1px solid gray", p: 2 }}>
                  <img src="https://picsum.photos/200/300" alt="" />
                  <motion.div key={5} layoutId={`product-${5}`} className={`bookEffect ${layoutIdSet === 1 && "active"}`} onClick={() => { setOpen(true), setlayoutIdSet(5) }}>
                    <div className="layer layerOne">
                      <span>M</span>
                    </div>
                    <div className="layer backLayer"></div>
                    <div className="coverLine"></div>
                  </motion.div>
                </Box>
              </Grid>

            </AnimatePresence>


          </Grid>
        </Container>
        <ModelBox open={open} setOpen={setOpen} handleOpen={handleOpen} handleClose={handleClose} layoutIdSet={layoutIdSet} />
      </>
    </>
  )
}

export default App


// --modal--
const ModelBox = ({ open, setOpen, handleClose, handleOpen, layoutIdSet }) => {

  return (
    <>

      <div>
        <Button onClick={handleOpen}>Open modal</Button>
        <Modal
          open={open}
          onClose={handleClose}
          aria-labelledby="modal-modal-title"
          aria-describedby="modal-modal-description"
        >
          <Box sx={style}>
            <Typography id="modal-modal-title" variant="h6" component="h2">
              <motion.div id={layoutIdSet} key={layoutIdSet} layoutId={`product-${layoutIdSet}`} className="bookEffect modelBook" onClick={() => setOpen(true)}>
                <div className="layer layerOne">
                  <span>M</span>
                </div>
                <div className="layer backLayer"></div>
                <div className="coverLine"></div>

              </motion.div>
            </Typography>
            <Typography id="modal-modal-description" sx={{ mt: 2 }}>
              Duis mollis, est non commodo luctus, nisi erat porttitor ligula.
            </Typography>
          </Box>
        </Modal>
      </div>
    </>
  )
}

